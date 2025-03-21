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
        dependencyCheckPublisher failedTotalCritical: 1, pattern: 'dependency-check-report.xml', stopBuild: true
        publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, icon: '', keepAll: true, reportDir: './', reportFiles: 'dependency-check-report.xml', reportName: 'OWASP HTML Report', reportTitles: '', useWrapperFileDirectly: true])      
      }  
    }
  }
}
