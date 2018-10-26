pipeline {
  agent any
  options {
    timestamps()
  }
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
              dir(path: '../../../test_jenkins/') {
                bat 'git fetch --all'               
                bat 'git reset --hard origin/test_jenkins'
                bat 'git pull origin test_jenkins'
              }
          }
          post {
            always {
              cleanWs()
              dir(path: '../../../test_jenkins@tmp') {
                deleteDir()
              }
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
              dir(path: '../../../test_jenkins/') {
                bat 'git fetch --all'               
                bat 'git reset --hard origin/test_jenkins'
                bat 'git pull origin test_jenkins'
              }
          }
          post {
            always {
              cleanWs()
              dir(path: '../../../test_jenkins@tmp') {
                deleteDir()
              }              
              dir(path: "${env.WORKSPACE}@tmp") {
                deleteDir()
              }
            }
          }
        }
      }
      post {
        always {
          echo 'Success'
        }
      }
    }
  }
}
