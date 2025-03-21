pipeline {
  agent any

  tools {
  nodejs 'node-23-9-0'
}

  stages {
    stage('install dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('OWSAP Dependency Check') {
      steps {
        dependencyCheck additionalArguments: '--format=XML', nvdCredentialsId: 'OWASP_API_KEY', odcInstallation: 'OWASP-12-1-0'
      }  
    }
  }
}
