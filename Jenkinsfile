pipeline {
  agent any
  stages {
    stage('1') {
      parallel {
        stage('1-1') {
          agent {
            node {
              label 'master'
            }

          }
          steps {
            timestamps() {
              dir(path: '/test_jenkins/') {
                bat 'dir'
              }

              bat 'dir'
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
              dir(path: '/test_jenkins') {
                bat 'dir'
              }

              bat 'dir'
            }

          }
        }
      }
    }
    stage('2') {
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

            echo '${env.WORKSPACE}'
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

            echo '${env.WORKSPACE}'
          }
        }
      }
    }
  }
}