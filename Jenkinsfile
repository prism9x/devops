pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Get code from a GitHub repository
                credentialsId: 'github',
                git url: 'https://github.com/prism9x/devops.git', branch: 'master'
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