pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(branch: 'main', credentialsId: 'github-creds', url: 'https://github.com/ayupazamat/cicd-pipeline.git')
        sh 'ls -la'
      }
    }

  }
}