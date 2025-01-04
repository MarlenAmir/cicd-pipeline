pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''chmod +x ./scripts/build.sh
./scripts/build.sh'''
      }
    }

    stage('test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('build docker image') {
      steps {
        sh 'docker build -t mydocker_image .'
      }
    }

    stage('push docker image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
            def app = docker.build("mydocker_image:${env.BUILD_NUMBER}")
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }
      }
    }
  }
}
