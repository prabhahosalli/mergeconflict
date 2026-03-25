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
      echo 'Running Container'
      sh 'docker run -d -p 9090:80 my-app'
    }
  }
}
}
