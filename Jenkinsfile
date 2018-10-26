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
  }
  post {
        always {
            cleanWs()
        }
    }
}
