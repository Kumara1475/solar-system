pipeline {
  agent any

  environment {
        MONGO_URI = "mongodb://localhost:27017/mydatabase"
    }

  tools {
  nodejs 'node-23-9-0'
}

  stages {
    stage('install dependencies') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'MONGO_CRED', passwordVariable: 'MONGO_PASSWORD', usernameVariable: 'MONGO_USERNAME')]) {
          sh 'npm test'
        }
      }
    }
    stage('OWSAP Dependency Check') {
      steps {
         dependencyCheck additionalArguments: '--format=HTML --format=XML', nvdCredentialsId: 'OWASP_API_KEY', odcInstallation: 'OWASP-12-1-0'
         publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, icon: '', keepAll: true, reportDir: './', reportFiles: 'dependency-check-report.html', reportName: 'Dependency check HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    
      }  
    }
    stage('unit testing') {
       steps {
        sh 'npm test'
       }
    }
  }
}
