pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          docker.build("my-app")
        }

      }
    }

    stage('Copy Git Repository') {
      steps {
        script {
          sh "git clone https://github.com/t-kviloria/cicd-pipeline"
          // Copy repository files to Docker container
          docker.withRegistry('https://registry.hub.docker.com', 'docker-creds') {
            docker.image('my-app').inside {
              sh "rm -rf /app/*"
              sh "cp -r /workspace/my-app/* /app"
            }
          }
        }

      }
    }

    stage('Build Application') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker-creds') {
            docker.image('my-app').inside {
              sh "cd /app && ./scripts/build.sh"
            }
          }
        }

      }
    }

    stage('Test Application') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker-creds') {
            docker.image('my-app').inside {
              sh "cd /app && ./scripts/test.sh"
            }
          }
        }

      }
    }

  }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}