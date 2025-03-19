pipeline {
  agent any

  tools {
    nodejs "node-23.9.0"
  }

  stages {
    stage('install dependencies') {
      steps {
        sh 'npm install'
      }
    }
  }
}
