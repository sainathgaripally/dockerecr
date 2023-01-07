pipeline {
    agent any
    environment {

    }
    stages {
        stage('login to ecr') {
            steps {
                script {
                    aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 307854153830.dkr.ecr.eu-central-1.amazonaws.com
                }
            }
        }
        stage ('Build Image') {
            steps {
                script {
                    docker build -t myproject .
                }
            }
        }
        stage ('Tag Image') {
            steps {
                script {
                    docker tag myproject:latest 307854153830.dkr.ecr.eu-central-1.amazonaws.com/myproject:latest
                }
            }
        }
        stage ('Push Image') {
            steps {
                script {
                    docker push 307854153830.dkr.ecr.eu-central-1.amazonaws.com/myproject:latest
                }
            }
        }
    }
}
