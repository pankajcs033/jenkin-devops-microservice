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
        stage('Fetch') { // mandatory
            steps { // mandatory
                sh 'mvn --version'
                // sh 'docker version'
                echo "Build"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_URL - $env.BUILD_URL"
            }
        }
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Integration Test') {
            steps {
                sh "mvn failsafe:integration-test failsafe:verify"
            }
        }
        stage('Package') {
            steps {
                sh "mvn package -DskipTests"
            }
        }
        stage('Docker build image') {
            steps {
                // docker build -t pankajcs033/currency-exchange-devops:$env.BUILD_TAG
                script {
                    dockerImage = docker.build("pankajcs033/currency-exchange-devops:${env.BUILD_TAG}")
                }
            }
        }
        stage('Docker push image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub') {
                        dockerImage.push();
                        dockerImage.push('latest');
                    }
                }
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
