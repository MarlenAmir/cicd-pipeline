pipeline {

  agent any

  stages {
    stage('TEST') {
      steps {
        git branch: 'main', credentialsId: 'github-creds', url: 'https://github.com/ayupazamat/cicd-pipeline.git'
      }
    }

  }
}