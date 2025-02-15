pipeline {
  agent any

  environment {
    CC = 'clang'
    jenkins_password = credentials('jenkins-agent-ssh')
  }

  parameters {
    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
  }

  triggers { pollSCM('H/2 * * * *') }

  options { buildDiscarder(logRotator(numToKeepStr: '3')) }

  stages {
    stage('One') {
      steps {
        sh 'echo Hello'
        sh 'echo Bye'
        sh 'env'
      }
    }

    stage('Example') {
      input {
        message "Should we continue?"
        ok "Yes, we should."
        parameters {
          string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        }
      }
      steps {
        echo "Hello, ${PERSON}, nice to meet you."
      }
    }

  }

  post {
    always {
      sh 'echo Post Step'
    }
  }

}
