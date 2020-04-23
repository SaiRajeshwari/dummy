def workspace
pipeline {
  agent any
  stages {
    stage('Build') {
      /* Intended to fail*/
      steps {
        Some wrong steps here
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