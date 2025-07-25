pipeline {
    agent any

    environment {
        IMAGE_NAME = "nodejs-cicd-demo"
        CONTAINER_NAME = "nodejs-app"
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR-USERNAME/nodejs-cicd-demo.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
                sh 'docker run -d --name $CONTAINER_NAME -p 3000:3000 $IMAGE_NAME'
            }
        }
    }
}
