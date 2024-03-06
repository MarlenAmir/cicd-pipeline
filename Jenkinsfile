pipeline {
  agent any
  stages {
    stage('Checkout GIT') {
      steps {
        git(url: 'https://github.com/ayupazamat/cicd-pipeline.git', branch: 'main', credentialsId: 'github-creds')
        sh 'docker --version'
      }
    }

    stage('Build') {
      steps {
        sh './scripts/build.sh'
      }
    }

  }
}