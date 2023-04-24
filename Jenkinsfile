pipeline {
  agent any
  stages {
    stage('Checkout code') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        chmod +x scripts/build.sh
        sh './scripts/build.sh'
      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
