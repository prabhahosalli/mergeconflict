pipeline {
    agent any

    environment {
        DOCKER_USER = 'prabha97hosalli@gmail.com'
        IMAGE_NAME = 'my-app'
    }

    stages {

        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Clone') {
            steps {
                git branch: 'master', url: 'https://github.com/prabhahosalli/mergeconflict.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_USER/$IMAGE_NAME:latest .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKER_USER/$IMAGE_NAME:latest'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f my-container || true'
                sh 'docker run -d -p 9090:80 --name my-container $DOCKER_USER/$IMAGE_NAME:latest'
            }
        }
    }
}

