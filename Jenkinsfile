pipeline {
  agent {
    docker {
      image 'node:16-alpine'
    }

  }
  stages {
    stage('build') {
      steps {
        sh ' npm install'
      }
    }

  }
}