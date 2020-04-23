def workspace
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo dummy'
        script {
          if (currentBuild.number % 2 == 0) {
            throw new Exception("Something went wrong!")
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