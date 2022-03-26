pipeline {
  agent any
  stages {
    stage('conf') {
      steps {
        sh 'ip ad'
      }
    }

    stage('testing') {
      steps {
        junit 'test'
      }
    }

  }
}