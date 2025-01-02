pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'sh \'./scripts/build.sh\''
      }
    }

    stage('test') {
      steps {
        sh 'sh \'./scripts/test.sh\''
      }
    }

  }
}