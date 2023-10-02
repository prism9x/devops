pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                scripts{
                    git credentialsId: 'github', url: 'https://github.com/prism9x/devops.git'
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Build Images...'
            }
        }
        stage('Pushing... to Docker Hub') {
            steps {
                echo 'Pushing... to Docker Hub'
            }
        }
    }
}