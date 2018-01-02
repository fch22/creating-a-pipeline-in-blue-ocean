pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }
    
  }
  stages {
    stage('proxy') {
      steps {
        sh '''npm config set proxy http://proxy.lbs.alcatel-lucent.com:8000
'''
      }
    }
  }
}