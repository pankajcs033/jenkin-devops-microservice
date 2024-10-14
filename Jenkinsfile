// DECLARATIVE
pipeline {
    agent any // mandatory
    // agent { docker { image 'node:20.18.0-alpine3.20'}}
    environment {
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    stages { // mandatory
        stage('Build') { // mandatory
            steps { // mandatory
                sh 'mvn --version'
                sh 'docker version'
                echo "Build"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_URL - $env.BUILD_URL"
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
