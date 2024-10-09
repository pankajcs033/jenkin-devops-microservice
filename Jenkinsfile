// DECLARATIVE
pipeline {
	// agent any // mandatory
	// agent { docker { image 'node:20.18.0-alpine3.20'}}
	stages { // mandatory
		stage('Build') { // mandatory
			steps { // mandatory
				// echo "Build"
				sh 'docker -v'
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
