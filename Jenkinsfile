pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('Build') {
      steps {
        sh 'chmod +x ./scripts/build.sh'
        sh './scripts/build.sh'
      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}