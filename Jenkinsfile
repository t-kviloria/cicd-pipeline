pipeline {
    agent any
    stages {
        stage('Build Docker image') {
            steps {
                script {
                    def dockerImage = docker.build('js-app', '--file Dockerfile .')
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage.inside {
                        sh '.scripts/build.sh'
                    }
                }
            }
        }
    }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
