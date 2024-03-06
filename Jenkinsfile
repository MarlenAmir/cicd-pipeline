pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/ayupazamat/cicd-pipeline.git', credentialsId: 'github-creds')
      }
    }

  }
}