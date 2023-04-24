pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'scripts/build.sh'
      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}