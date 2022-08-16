pipeline {
  agent none
  stages {
    stage('Init') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        sleep(time: 1, unit: 'SECONDS')
      }
    }

  }
}