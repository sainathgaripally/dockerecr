pipeline {
    agent any
    environment {
        AWS_REGION = "eu-central-1"
    }
    stages {
        stage('logging to ecr') {
            steps {
                sh "aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 307854153830.dkr.ecr.${AWS_REGION}.amazonaws.com"
            }
        }
        stage('build image') {
            steps {
                sh "docker build -t myrepo ."
            }
        }
        stage('tag image') {
            steps {
                sh "docker tag myrepo:latest 307854153830.dkr.ecr.${AWS_REGION}.amazonaws.com/myproject:latest"
            }
        }
        stage('push to repo') {
            steps {
                sh "docker push 307854153830.dkr.ecr.eu-central-1.amazonaws.com/myproject:latest"
            }
        }
    }
}

