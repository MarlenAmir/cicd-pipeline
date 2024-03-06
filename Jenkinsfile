pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        git(url: 'https://github.com/ayupazamat/cicd-pipeline.git', branch: 'main', credentialsId: 'github-creds')
      }
    }

  }
}