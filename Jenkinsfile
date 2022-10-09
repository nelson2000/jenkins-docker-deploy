pipeline {
  agent none
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t nwajienelson/nx-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push nwajienelson/nx-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
