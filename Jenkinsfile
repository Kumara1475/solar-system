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
         dependencyCheck additionalArguments: '--format=HTML --format=XML', nvdCredentialsId: 'OWASP_API_KEY', odcInstallation: 'OWASP-12-1-0'
         publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, icon: '', keepAll: true, reportDir: './', reportFiles: 'dependency-check-report.html', reportName: 'Dependency check HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    
      }  
    }
    stage('unit testing') {
      sh 'npm test'
    }
  }
}
