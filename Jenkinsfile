pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }
    
  }
  stages {
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
    stage('Test') {
      steps {
        sh 'sh \'./jenkins/scripts/test.sh\''
      }
    }
  }
}