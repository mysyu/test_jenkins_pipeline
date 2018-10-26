pipeline {
  agent any
   stages{
    stage('1') {
      parallel {
        stage('1-1') {
          agent {
            node {
              label 'master'
            }
          }
          steps {
              dir(path: '/test_jenkins/') {
                bat 'dir'
              }
              bat 'dir'
          }
          post {
            always {
              cleanWs()
              dir(path: "${env.WORKSPACE}@tmp") {
                deleteDir()
              }
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
              dir(path: '/test_jenkins/') {
                bat 'dir'
              }
              bat 'dir'
          }
          post {
            always {
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
