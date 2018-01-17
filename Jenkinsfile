pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }
    
  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          environment {
            https_proxy = 'http://proxy.lbs.alcatel-lucent.com:8000'
          }
          steps {
            sh '''npm config set https-proxy http://proxy.lbs.alcatel-lucent.com:8000
'''
            sh '''npm config list -l
'''
            sh '''npm install
'''
          }
        }
        stage('buikld 1') {
          steps {
            echo 'hello word'
          }
        }
      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh '''./jenkins/scripts/deliver.sh
'''
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh '''./jenkins/scripts/kill.sh
'''
      }
    }
  }
  environment {
    CI = 'true'
  }
}