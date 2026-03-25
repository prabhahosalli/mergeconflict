pipeline {
  agent any

stages {

  stage('clone') {
    steps {
      echo 'Cloning code'
    } 
  }

  stage('Build docker image') {
    steps {
      echo 'Building docker image'
      sh 'docker build --no-cache -t my-app .'
    }
  }

  stage('Run Container') {
    steps {
      echo 'Stopping old Container'
      sh 'docker rm -f my-container || true'

      echo 'Running new container'
      sh 'docker run -d -p 9090:80 --name my-container my-app'
    }
  }
}
}
