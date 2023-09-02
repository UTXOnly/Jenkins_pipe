pipeline {
    agent any

    stages {

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
                    sh "curl http://localhost:8003"
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
