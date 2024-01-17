pipeline{
  agent any
  environment{
    DOCKERHUB_CREDENTIALS = credentials('althamashn-dockerhub')
  }
  stages{
    stage('Build'){
      steps{
        bat 'docker build -t althamash/project:latest'
      }
    }
    stage('Login'){
      steps{
        bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push'){
      steps{
        bat 'docker push althamash/project:latest'
      }
    }
  }
  post{
      always{
        bat 'docker logout'
      }
    }
}
