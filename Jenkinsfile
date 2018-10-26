pipeline {
  agent any
  stages {
    stage('1-1') {
      parallel {
        stage('1-1') {
          agent {
            node {
              label 'master'
            }

          }
          steps {
            timestamps() {
              bat 'cd /test_jenkins/ && dir'
            }

          }
        }
        stage('1-2') {
          steps {
            timestamps() {
              bat 'cd /test_jenkins/ && dir'
            }

          }
        }
      }
    }
  }
}