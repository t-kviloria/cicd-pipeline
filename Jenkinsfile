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
        sh chmod +x ./scripts/hello.sh && sh './scripts/hello.sh'
      }
    }
  }
    environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
