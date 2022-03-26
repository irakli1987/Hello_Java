pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        echo 'Placeholder'
        sh 'echo Edited Placeholder'
        sh './gradlew build'
      }
    }

    stage('Fluffy test') {
      steps {
        echo 'Placeholder'
        sh 'sleep 5'
        sh 'echo pwd'
      }
    }

    stage('Testing A') {
      steps {
        sh './gradlew check'
        echo 'Running Unit Tests'
        sleep 5
      }
    }

  }
  post {
    always {
      archiveArtifacts(artifacts: 'build/libs/**/*.jar', fingerprint: true)
      junit 'build/reports/**/*.xml'
    }

  }
}