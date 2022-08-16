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
        echo 'test'
      }
    }

  }
}