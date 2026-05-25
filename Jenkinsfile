@"
pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo "Corriendo en rama: \${env.BRANCH_NAME}"
      }
    }

    stage('Validacion de PR') {
      when {
        changeRequest()
      }
      steps {
        echo "PR desde \${env.CHANGE_BRANCH} hacia \${env.CHANGE_TARGET}"
      }
    }
  }

  post {
    success { echo "Pipeline verde" }
    failure { echo "Pipeline rojo" }
  }
}
"@ | Out-File -FilePath Jenkinsfile -Encoding utf8