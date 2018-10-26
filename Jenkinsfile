pipeline {
  agent any
  timestamps() {
    stages {
      stage('1') {
        parallel {
          stage('1-1') {
            agent {
              node {
                label 'master'
              }
            }
            try {
              steps {
                  dir(path: '/test_jenkins/') {
                    bat 'dir'
                  }
                  bat 'dir'
              }
            }
            finally {
              cleanWs()
              dir(path: "${env.WORKSPACE}@tmp") {
                deleteDir()
              }
            }
          }
          stage('1-2') {
            agent {
              node {
                label 'node2'
              }
            }
            try {
              steps {
                  dir(path: '/test_jenkins/') {
                    bat 'dir'
                  }
                  bat 'dir'
              }
            }
            finally {
              cleanWs()
              dir(path: "${env.WORKSPACE}@tmp") {
                deleteDir()
              }
            }
          }
        }
      }
    }
  }
}
