pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Application Build') {
      steps {
        script {
          def appImage = docker.build("${registry}:${env.BUILD_ID}")
          appImage.inside {
            sh './scripts/build.sh'
          }
        }
      }
    }

    stage('Tests') {
      steps {
        script {
          def appImage = docker.build("${registry}:${env.BUILD_ID}")
          appImage.inside {
            sh './scripts/test.sh'
          }
        }
      }
    }

    stage('Docker Image Build') {
      steps {
        script {
          def appImage = docker.build("${registry}:${env.BUILD_ID}")
          appImage.push()
        }
      }
    }
  }

  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
