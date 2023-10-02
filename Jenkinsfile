pipeline {
    agent any
    environment{
        GITHUB_ACCESS_KEY = credentials('github')
        DOCKER_HUB_ACCESS_KEY = credentials('docker-hub')

        REGISTRY = "prism9x/devops-automation"
        dockerImage = ''
    }
    stages {
        stage('Checkout') {
            steps {
                // Get code from a GitHub repository
                git url: 'https://github.com/prism9x/devops.git', branch: 'master', credentialsId: GITHUB_ACCESS_KEY
            }
        }
        stage('Build Images') {
            steps {
                scripts {
                    dockerImage = docker.Build REGISTRY
                }
            }
        }
        stage('Deploy Images') {
            steps {
                script {
                    docker.withRegistry( '', DOCKER_HUB_ACCESS_KEY ) {
                            dockerImage.push()
                        }
                }
            }
        }
    }
}