pipeline {
  agent any
  stages {
    stage('Build Docker image') {
      steps {
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('Build') {
      steps {
        script {
          sh 'chmod +x ./scripts/build.sh'
          echo "Running build.sh script"
          sh ' ./scripts/build.sh'
        }

      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}