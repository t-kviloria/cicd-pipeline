pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/KonstantinFomenko/cicd-pipeline', branch: 'main')
      }
    }

    stage('App Build') {
      steps {
        script {
          sh 'chmod +x ./scripts/build.sh'
          sh './scripts/build.sh'
        }

      }
    }

    stage('Tests') {
      steps {
        script {
          sh 'chmod +x ./scripts/test.sh'
          sh './scripts/test.sh'
        }

      }
    }

    stage('Docker Image Build') {
      steps {
        script {
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('Push Docker Image') {
        steps {
            script {
                def dockerImage = docker.build("${registry}:${env.BUILD_ID}")
                docker.withRegistry('', 'dockerhub-id') {
                    dockerImage.push()
                }
            }
        }
     }

    }
  environment {
    registry = 'itemo/practical_task_ci_cd'
  }
