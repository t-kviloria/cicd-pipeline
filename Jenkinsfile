pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          scripts/build.sh
        }

      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
