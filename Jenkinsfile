// DECLARATIVE
pipeline {
	// agent any // mandatory
	agent { 
		docker { 
				image 'maven:3.9.3-eclipse-temurin-17'
            	args '-v $HOME/.m2:/root/.m2'
				}
		}
	stages { // mandatory
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
