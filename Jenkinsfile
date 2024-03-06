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
        sh '''chmod +x scripts/build.sh

'''
        sh './scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x scripts/test.sh
'''
        sh './scripts/test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build -t mybuildimage  .'
      }
    }


  }
}