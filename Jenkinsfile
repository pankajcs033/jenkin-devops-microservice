// DECLARATIVE
pipeline {
    // agent any // mandatory
    agent none
    stages { // mandatory
        stage('Maven Install') {
        agent {
            docker {
            image 'maven:3.5.0'
            }
        }
        steps {
            sh 'mvn clean install'
        }
        }
        stage('Build') { // mandatory
            steps { // mandatory
                // echo "Build"
                sh 'mvn --version'
            }
        }
        stage('Test') {
            steps {
                echo "Test"
            }
        }
        stage('Integration Test') {
            steps {
                echo "Integration Test"
            }
        }
    }
    post {
        always {
            echo 'I run always'
        }
        success {
            echo 'I run when you success'
        }
        failure {
            echo 'I run when you fail'
        }
    }
}
