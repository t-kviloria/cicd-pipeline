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
         docker.image("${registry}:${env.BUILD_ID}").inside {c ->
          sh 'chmod +x ./scripts/build.sh'
          sh './scripts/build.sh'}
          }
        }
      }

    }
    environment {
      registry = 'itemo/practical_task_ci_cd'
    }
}
