pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Application Build') {
            steps {
                sh 'chmod +x ./scripts/build.sh'
                sh './scripts/build.sh'
            }
        }

        stage('Tests') {
            steps {
                sh 'chmod +x ./scripts/test.sh'
                sh './scripts/test.sh'
            }
        }

        stage('Docker Image Build') {
            steps {
                sh "docker build -t your-image-name ."
            }
        }
    }

  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
