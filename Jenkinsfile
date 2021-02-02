pipeline {
  agent any

  tools {nodejs "node"}

  stages {
    stage('Inicio +Install dependencies') {
      steps {
        slackSend (color: '#731CE8', message: "${GIT_COMMITTER_NAME} ha hecho un comit en la rama ${GIT_LOCAL_BRANCH}. LINK: ${GIT_URL}")
        sh 'npm install'
        slackSend (color: '#00FF00', message: "Instalación de dependencias")
      }
    }
     
    stage('Test') {
      steps {
         sh 'npm run coverage'
         slackSend (color: '#00FF00', message: "Tests")
      }
    }

    stage('SonarQube analysis') {
        steps {
            script {
                scannerHome = tool 'SonarQube Scanner 4.6.0.2311'
            }
            withSonarQubeEnv('SonarQube') {
            sh "${scannerHome}/bin/sonar-scanner"
            }
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
