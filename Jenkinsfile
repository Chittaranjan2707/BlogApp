pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'DockerhubCred'
        REPO_URL = 'https://github.com/Chittaranjan2707/BlogApp'
        FRONT_IMAGE = 'chittaranjan27/front-app'
        BACK_IMAGE = 'chittaranjan27/back-app'
    }

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: env.REPO_URL, branch: 'main'
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('blogFrontend') {
                    script {
                        docker.build(env.FRONT_IMAGE)
                    }
                }
            }
        }

        stage('Build Backend Application') {
            steps {
<<<<<<< HEAD
                dir('blogBackend') {
                    // Run Maven build
=======
                dir('back') {
>>>>>>> 733a56a (Kubernetes)
                    sh 'mvn clean package'
                }
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                dir('blogBackend') {
                    script {
                        docker.build(env.BACK_IMAGE, '.')
                    }
                }
            }
        }

        stage('Push Docker Images to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', env.DOCKER_CREDENTIALS_ID) {
                        docker.image(env.FRONT_IMAGE).push('latest')
                        docker.image(env.BACK_IMAGE).push('latest')
                    }
                }
            }
        }

        stage('Deploy with Ansible') {
            steps {
                script {
                    sh 'ansible-playbook -i ansible/hosts ansible/playbooks/deploy-mysql.yml'
                    sh 'ansible-playbook -i ansible/hosts ansible/playbooks/deploy-backend.yml'
                    sh 'ansible-playbook -i ansible/hosts ansible/playbooks/deploy-frontend.yml'
                }
            }
        }
    }
}

