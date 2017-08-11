pipeline {
  agent none
  stages {
    stage('Checkout') {
      agent { label 'docker' }
      steps {
        echo 'Checkout'
      }
    }
    stage('Build') {
      agent { label 'docker' }
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
      agent {
        docker {
          image 'maven:3-alpine'
          label 'docker'
        } 
      }
      steps {
        echo 'Deploying Apps'
      }
    }
  }
  environment {
    qa = ''
  }
}
