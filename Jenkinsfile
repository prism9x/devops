pipeline {
    agent any
    environment{
        GITHUB_ACCESS_KEY = credentials('github')
        DOCKER_HUB_ACCESS_KEY = credentials('docker-hub')
    }
    stages {
        stage('Clone repository') {
            steps {
                // Get code from a GitHub repository
                git url: 'https://github.com/prism9x/devops.git', branch: 'master', credentialsId: GITHUB_ACCESS_KEY
            }
        }
        // stage('Build') {
        //     steps {
        //         echo 'Build Images...'
        //     }
        // }
        // stage('Pushing... to Docker Hub') {
        //     steps {
        //         echo 'Pushing... to Docker Hub'
        //     }
        // }
    }
}