// DECLARATIVE
pipeline {
	agent any // mandatory
	stages { // mandatory
		stage('Build') { // mandatory
			steps { // mandatory
				echo "Build"
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
