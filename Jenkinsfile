pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Sleep') {
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