def workspace
pipeline {
  agent any
  stages {
    stage('Build') {
      /* Intended to fail*/
      steps {
        catchError {
           Some wrong steps here
        }
        post {
          success {
             echo 'Build stage successful'
          }
          failure {
             echo 'Build stage failed'
          }
        }
      }
    }
  }
  post {
    always {
      echo "Result: ${currentBuild.currentResult}"
      logstashSend failBuild: true, maxLines: 1000
    }
  }
}