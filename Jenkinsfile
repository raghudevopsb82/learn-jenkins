node {

  stage('Run-for-all') {
      echo 'This stage will be executed first.'
      sh 'env'
  }

  if("${BRANCH_NAME}" == "main") {
    stage('Run-for-main') {
      echo 'This stage will be executed first.'
    }
  } else if("${BRANCH_NAME}" =~ "PR-.*") {
    stage('Run-for-PR') {
      echo 'This stage will be executed first.'
    }
  } else {
    stage('Run-for-dev') {
      echo 'This stage will be executed first.'
    }
  }

}

