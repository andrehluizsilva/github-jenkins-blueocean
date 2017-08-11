pipeline {
  agent none
  stages {
    stage('Checkout') {
      agent {
        label 'docker'
      }
      steps {
        echo 'Checkout'
      }
    }
    stage('Build') {
      agent {
        label 'docker'
      }
      steps {
        echo 'Building App'
        sleep 2
        isUnix()
      }
    }
    stage('Test') {
      agent any
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
      agent {
        docker {
          image 'maven:3-alpine'
          label 'docker'
        }
        
      }
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