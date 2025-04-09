pipeline {
    agent any

    environment {
        IMAGE_NAME = 'avbharadwaj/my-image'
        CONTAINER_NAME = 'myapp'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Stop Old Container (if exists)') {
            steps {
                script {
                    sh 'docker rm -f $CONTAINER_NAME || true'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d --name $CONTAINER_NAME -p 8090:80 $IMAGE_NAME'
                }
            }
        }
    }
}

