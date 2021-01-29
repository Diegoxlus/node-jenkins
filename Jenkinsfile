pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {

    stage('Travis Start') {
      steps {
         slackSend (color: '#FFFF00', message: "INICIO: Tarea '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm install'
        slackSend (color: '#00FF00', message: "Instalación de dependencias")
      }
    }
     
    stage('Test') {
      steps {
         sh 'npm test'
         slackSend (color: '#00FF00', message: "Tests")
      }
    }      
  }
  post {
    success{
        slackSend (color: '#00FF00', message: ":white_check_mark:INTEGRACIÓN CORRECTA :white_check_mark:")
    }
    failure {
        slackSend (color: '#00FF00', message: ":red_circle: INTEGRACIÓN INCORRECTA :red_circle:")
    }
  }
}
