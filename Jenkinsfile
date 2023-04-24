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
        sudo sh './scripts/build.sh'
      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
