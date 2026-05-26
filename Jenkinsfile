pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo "Corriendo en rama: ${env.BRANCH_NAME}"
      }
    }

    stage('Validacion de PR') {
      when {
        changeRequest()
      }
      steps {
        echo "PR desde ${env.CHANGE_BRANCH} hacia ${env.CHANGE_TARGET}"
        error("fallo intencional")
      }
    }
  }

  post {
    success { echo "Pipeline verde" }
    failure { echo "Pipeline rojo" }
  }
}