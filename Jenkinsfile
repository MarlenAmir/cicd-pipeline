pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''stage(\'Build\') {
    steps {
        sh \'./scripts/build.sh\'  
    }
}
'''
        }
      }

    }
  }