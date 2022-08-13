node {
    docker.image('node:lts-bullseye-slim').inside('-p 3000:3000') {
        stage('Checkout source code') {
            checkout scm
        }
        stage('Build') {      
            sh 'npm install'     
        }      
        stage('Test') {
            sh './jenkins/scripts/test.sh' 
        }  
        stage("Manual Approval") {
            input message: 'Lanjutkan ke tahap Deploy?'
        }
        stage('Deploy') {          
            sh './jenkins/scripts/deliver.sh'
            sleep 60
            sh './jenkins/scripts/kill.sh'            
        }     
    }
}