pipeline {
  agent any
  stages {
    stage('Checkout GIT') {
      steps {
        git(url: 'https://github.com/ayupazamat/cicd-pipeline.git', branch: 'main', credentialsId: 'github-creds')
      }
    }

    stage('Build') {
      steps {
        sh 'chmod +x scripts/build.sh'
        sh './scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'chmod +x scripts/test.sh'
        sh './scripts/test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build -t a3ukjke/epam-cicd  .'
      }
    }

    stage('Test docker image') {
      environment {
        DOCKERHUB_CREDENTIALS_PSW = credentials('dockerhub_id')
      }
      steps {
        sh "docker build -t a3ukjke/epam-cicd:$BUILD_NUMBER ."
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin docker.io'
        sh 'docker push a3ukjke/epam-cicd:$BUILD_NUMBER'
        sh 'docker logout'
      }
    }

  }
}