pipeline {
    agent {
        docker {
            image 'docker:latest'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/t-kviloria/cicd-pipeline']]])
            }
        }
        stage('Build') {
            steps {
                sh './scripts/build.sh'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t practical_task_ci_cd .'
            }
        }
    }
}

  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
}
