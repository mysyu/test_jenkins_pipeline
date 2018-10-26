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
          agent {
            node {
              label 'node2'
            }

          }
          steps {
            timestamps() {
              bat 'cd /test_jenkins/ && dir'
            }

          }
        }
      }
    }
    stage('2-1') {
      parallel {
        stage('2-1') {
          agent {
            node {
              label 'master'
            }

          }
          steps {
            timestamps() {
              cleanWs(deleteDirs: true)
            }

          }
        }
        stage('2-2') {
          agent {
            node {
              label 'node2'
            }

          }
          steps {
            timestamps() {
              cleanWs(deleteDirs: true)
            }

          }
        }
      }
    }
  }
}