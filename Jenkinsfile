pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Define the Docker image name
                    def imageName = 'hello-world'

                    // Build the Docker image using Docker Compose
                    sh "docker-compose build --pull"

                    // Tag the Docker image with a unique version
                    sh "docker tag ${imageName} ${imageName}:${env.BUILD_NUMBER}"
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Start the container using Docker Compose
                    sh "docker-compose up -d"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Wait for the container to start
                    sleep 10

                    // Run a test command inside the container
                    sh "docker-compose exec ${imageName} echo 'Hello, World!'"
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    // Stop and remove the container using Docker Compose
                    sh "docker-compose down"
                }
            }
        }
    }
}
