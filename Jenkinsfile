pipeline {
  agent any
  stages {
    stage('One') {
      steps {
        sh 'echo Hello'
        sh 'echo Bye'
      }
    }
  }

  post {
    always {
      sh 'echo Post Step'
    }
  }

}
