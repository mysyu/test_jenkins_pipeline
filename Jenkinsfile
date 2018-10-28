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
              dir(path: "${WORKSPACE}@tmp") {
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
              dir(path: "${WORKSPACE}@tmp") {
                deleteDir()
              }
            }
          }
        }
      }
      post {
        always {
          script {
            emailext (
              subject: "${JOB_NAME} - Build # ${BUILD_NUMBER} - ${currentBuild.currentResult}! ${BUILD_TIMESTAMP}",
              body: "${JOB_NAME} - Build # ${BUILD_NUMBER} - ${currentBuild.currentResult}:\n\nCheck console output at ${BUILD_URL} to view the results.\n\n${BUILD_TIMESTAMP}",
              to: "testjenkins8001@gmail.com",
              attachLog: false
            )
          }
          build job: 'test_jenkins_unit_test', parameters: [string(name: 'url', value: 'http://140.116.82.145:8080')], wait: false
          build job: 'test_jenkins_unit_test', parameters: [string(name: 'url', value: 'http://140.116.138.69:8080')], wait: false
        }
      }
    }
  }
}
