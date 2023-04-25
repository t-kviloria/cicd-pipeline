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
        sh 'chmod +x ./scripts/build.sh'
        sh 'cat ./scripts/build.sh'
      }
    }
  }
    environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
