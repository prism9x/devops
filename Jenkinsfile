pipeline {
   agent any

   environment {
       CONTAINER_REGISTRY= credentials('docker-hub-key')
       CONTAINER_REPOSITORY= "prism9x"
       APPLICATION_SOURCE_URL = 'https://github.com/prism9x/devops.git'
       APPLICATION_NAME = "nginx-service"
       CONTAINER_BUILD_CONTEXT = "."
//        CONTAINER_REGISTRY_USER    = credentials('prism9x')
//        CONTAINER_REGISTRY_PASSWORD    = credentials('dckr_pat_2l1mCClB49uwEcIVEZpqJgTm1n8')
       APPLICATION_DOMAIN="https://example.com"
   }
   stages {
       stage ('Git Checkout') {

           steps {
               echo 'Git Checkout'            
               git branch: 'master',
                   url: "${APPLICATION_SOURCE_URL}"
                   // credentialsId: 'githubToken'
               script {
               GIT_COMMIT = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%h'").trim()
               }
           }
       }
       stage('Build') {
           steps {
               echo 'Building..'
               withDockerRegistry([credentialsId: "CONTAINER_REGISTRY", url: ""]) {
                   sh "docker build -t ${CONTAINER_REPOSITORY}/${APPLICATION_NAME}:${GIT_COMMIT} ${CONTAINER_BUILD_CONTEXT}"
                   sh "docker push ${CONTAINER_REPOSITORY}/${APPLICATION_NAME}:${GIT_COMMIT}"
               }
           }
       }
       stage('Deploy') { 
           steps {
               echo 'Deploying....'
           }
       }
   }
   post { 
       always { 
           cleanWs()
       }
   }
}