pipeline {
  agent any

  environment {
    CC = 'clang'
    jenkins_password = credentials('jenkins-agent-ssh')
  }

  options { buildDiscarder(logRotator(numToKeepStr: '3')) }

  stages {
    stage('One') {
      steps {
        sh 'echo Hello'
        sh 'echo Bye'
        sh 'env'
      }
    }
  }

  post {
    always {
      sh 'echo Post Step'
    }
  }

}
