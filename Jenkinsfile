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
        sh '''chmod +x scripts/build.sh'''
        sh './scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x scripts/test.sh'''
        sh './scripts/test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build -t a3ukjke/epam-cicd  .'
      }
    }

    stage('Push docker image') {
      steps {
      	withCredentials([usernamePassword(credentialsId: 'dockerhub_id', passwordVariable: 'dockerhub_idPassword', usernameVariable: 'dockerhub_idUser')]) {
        	sh "docker login -u ${env.dockerhub_idUser} -p ${env.dockerhub_idPassword}"
          sh 'docker push a3ukjke/epam-cicd:latest'
      }
    }


  }
}
}