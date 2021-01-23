pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {

    stage('Cloning Git') {
      steps {
        slackSend (color: '#FFFF00', message: "INICIO: Tarea '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        git 'https://github.com/Diegoxlus/node-jenkins'
      }
    }
        
    stage('Install dependencies') {
      steps {
        sh 'npm install'
        sh 'npm install --save-dev chai'
        slackSend (color: '#FF0000', message: "Instalación de dependencias")
      }
    }
     
    stage('Test') {
      steps {
         sh 'npm test'
         slackSend (color: '#FF0000', message: "Tests")
      }
    }      
  }
}
