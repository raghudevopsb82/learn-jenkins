//pipeline {
//  agent any
//
//  environment {
//    CC = 'clang'
//    jenkins_password = credentials('jenkins-agent-ssh')
//  }
//
//  parameters {
//    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
//    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
//    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
//    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
//    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
//  }
//
//  triggers { pollSCM('H/2 * * * *') }
//
//  options { buildDiscarder(logRotator(numToKeepStr: '3')) }
//
//  stages {
//    stage('One') {
//      steps {
//        sh 'echo Hello'
//        sh 'echo Bye'
//        sh 'env'
//      }
//    }
//
//    stage('Example') {
//      when {
//        environment name: 'CC', value: 'ABC'
//      }
////      input {
////        message "Should we continue?"
////        ok "Yes, we should."
////        parameters {
////          string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
////        }
////      }
//      steps {
//        echo "Hello, ${PERSON}, nice to meet you."
//      }
//    }
//
//  }
//
//  post {
//    always {
//      sh 'echo Post Step'
//    }
//  }
//
//}


//pipeline {
//  agent any
//  stages {
//    stage('Non-Parallel Stage') {
//      steps {
//        echo 'This stage will be executed first.'
//      }
//    }
//    stage('Parallel Stage') {
//      failFast true
//      parallel {
//        stage('Branch A') {
//          agent {
//            label "for-branch-a"
//          }
//          steps {
//            echo "On Branch A"
//          }
//        }
//        stage('Branch B') {
//          agent {
//            label "for-branch-b"
//          }
//          steps {
//            echo "On Branch B"
//          }
//        }
//        stage('Branch C') {
//          stages {
//            stage('Nested 1') {
//              steps {
//                echo "In stage Nested 1 within Branch C"
//              }
//            }
//            stage('Nested 2') {
//              steps {
//                echo "In stage Nested 2 within Branch C"
//              }
//            }
//          }
//        }
//      }
//    }
//  }
//}
//

pipeline {
  agent any

  stages {

    stage('Run-for-all') {
      steps {
        echo 'This stage will be executed first.'
        sh 'env'
      }
    }

    stage('Run-for-main') {
      when {
        branch 'main'
      }
      steps {
        echo 'This stage will be executed first.'
        sh 'env'
      }
    }

    stage('Run-for-dev') {
      when {
        allOf {
          expression { BRANCH_NAME != "main" }
          expression { BRANCH_NAME !=~ "PR-.*" }
        }

      }
      steps {
        echo 'This stage will be executed first.'
        sh 'env'
      }
    }

    stage('Run-for-pr') {
      when {
        expression { BRANCH_NAME ==~ "PR-.*" }
      }
      steps {
        echo 'This stage will be executed first.'
        sh 'env'
      }
    }


  }
}

//