pipeline {
  agent {
    label 'java'
  }
  stages {
    stage('Buzz Build') {
      environment {
        LOCAL_STAGE_VAR = '1'
      }
      steps {
        echo 'Bee name is $BUZZ_NAME'
        sh 'echo "Worker name $BUZZ_NAME"'
        sh 'echo "Workspace location is $WORKSPACE"'
        sh './jenkins/build.sh'
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true)
      }
    }

    stage('Buzz Test') {
      parallel {
        stage('Buzz Test') {
          steps {
            sh './jenkins/test-all.sh'
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('Testing A') {
          agent {
            label 'jre8'
          }
          steps {
            echo 'Running Unit Tests'
            sleep 5
          }
        }

        stage('Testing B') {
          steps {
            echo 'Running Int Tests'
            sleep 10
          }
        }

      }
    }

  }
  environment {
    BUZZ_NAME = 'Worker Bee'
  }
}