pipeline {
  agent any
  
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh './scripts/hello.sh'
      }
    }
  }
    environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
