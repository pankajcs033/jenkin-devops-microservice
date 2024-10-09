pipeline {
    agent {
        docker {
            image 'docker:latest'  // Docker image with Docker, but no Compose or curl
            args '-v /var/run/docker.sock:/var/run/docker.sock'  // Bind Docker socket
        }
    }

    stages {

        stage('Build Docker Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Run API Tests') {
            steps {
                sh 'docker exec lms-api-automation /bin/sh -c "mvn clean test"'
            }
        }

        stage('Generate Report') {
            steps {
                sh 'docker cp lms-api-automation:/home/apiautomation/testrun-reports ./testrun-reports'
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'testrun-reports/*', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            sh 'docker compose down'
        }
    }
}