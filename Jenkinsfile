pipeline {
  agent any

stages {

  stage('clone') {
    steps {
      echo 'Cloning code'
      git branch: 'master', url:
    'https://github.com/prabhahosalli/mergeconflict.git'     
    } 
  }
  
   stage('Debug'){
     steps {
       sh 'pwd'
       sh 'ls -l'
     }
   }
  
  stage('Build docker image') {
    steps {
      sh 'pwd'
      sh 'ls -l'
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
