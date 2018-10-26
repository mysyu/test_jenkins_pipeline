pipeline {
  agent any
   stages{
    stage('Deploy') {
      parallel {
        stage('140.116.82.145') {
          agent {
            node {
              label 'master'
            }
          }
          steps {
              dir(path: '/test_jenkins/') {
                bat 'dir'
              }
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
        stage('140.116.138.69') {
          agent {
            node {
              label 'node2'
            }
          }
          steps {
              dir(path: '/test_jenkins/') {
                bat 'dir'
              }
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
