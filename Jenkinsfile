pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh './scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('build docker image') {
      steps {
        sh 'docker build -t my_image .'
      }
    }

    stage('push docker image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
            def app = docker.build("my_image:${env.BUILD_NUMBER}")
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }
      }
    }
  }
}
