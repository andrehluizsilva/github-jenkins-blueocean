pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Checkout'
      }
    }
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
            error 'Error'
            
          },
          "Test 2": {
            catchError() {
              timeout(time: 5) {
                sleep 20
              }
              
            }
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying Apps'
        input(message: 'Waiting for deploy', submitter: 'admin', submitterParameter: 'OK', ok: 'OK')
      }
    }
  }
  environment {
    qa = ''
  }
}
