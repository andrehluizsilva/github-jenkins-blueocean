pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building App'
        sleep 2
        isUnix()
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test 1": {
            echo 'Testing 1'
            
          },
          "Test 2": {
            timeout(time: 2) {
              sleep 10
            }
            
            
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