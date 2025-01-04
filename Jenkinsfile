pipeline {
  agent any
  environment {
    DOCKER_IMAGE = "amirmarlen7/marlenamir_docker_image"
    DOCKER_TAG = "${env.BUILD_NUMBER}"
  }
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x ./scripts/build.sh
./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          // Build Docker image with the tag as the Jenkins build number
          docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
        }
      }
    }

    stage('Push Docker Image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
            def app = docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
            app.push("${DOCKER_TAG}")
            app.push("latest")  
          }
        }
      }
    }
  }
}
