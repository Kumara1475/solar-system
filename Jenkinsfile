pipeline {
  agent any

  tools {
    nodejs "node-23.9.0"
  }

  stages {
    stage('Node Version') {
      steps {
        sh '''
          node -v
          npm -v
        '''
      }
    }
  }
}
