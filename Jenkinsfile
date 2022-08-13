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
        stage('Deploy') {          
            sh './jenkins/scripts/deliver.sh'
            input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
            sh './jenkins/scripts/kill.sh'            
        }     
    }
}