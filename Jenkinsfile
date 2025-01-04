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

    stage('Push docker image') {
      steps {
        script {
      // Используем ваш репозиторий на Docker Hub
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
        // Собираем образ с тегом, включающим BUILD_NUMBER
            def app = docker.build("amirmarlen7/marlenamir_docker_image:${env.BUILD_NUMBER}")
        
        // Пушим образ с BUILD_NUMBER
            app.push("${env.BUILD_NUMBER}")
        
        // Пушим образ с тегом "latest"
            app.push("latest")
      }
    }
  }
}

  }
}
