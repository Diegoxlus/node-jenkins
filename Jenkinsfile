pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {

    stage('Cloning Git') {
      steps {
        slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        git 'https://github.com/Diegoxlus/node-jenkins'
      }
    }
        
    stage('Install dependencies') {
      steps {
        sh 'npm install'
        sh 'npm install --save-dev chai'

      }
    }
     
    stage('Test') {
      steps {
         sh 'npm test'
      }
    }      
  }
}
