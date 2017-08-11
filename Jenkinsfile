pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        parallel(
          "Build 1": {
            echo 'Building App'
            sleep 2
            isUnix()
            
          },
          "Build 2": {
            echo 'Build another app'
            
          }
        )
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test 1": {
            echo 'Testing 1'
            
          },
          "Test 2": {
            sleep 5
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying Apps'
      }
    }
  }
  environment {
    qa = ''
  }
}