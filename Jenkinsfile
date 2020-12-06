// Declarative script - > Does not require a node like a Scripted script
// Instead of keyword Node we use Pipeline
// Stages , stage and steps are mandatory for a declarative script
pipeline{
	// agent is where the build is going to run
	agent any 
	stages {
		stage("Build") {
			steps {
				echo "Build"
			}
		}post {
			success {
				echo " Fairly Expected!!!"
			}
		}
		stage("Test") {
			steps {
				echo " Test"
			}
		}post {
			always {
				echo " Excellent stuff!!!"
			}
		}
		stage("Integration Test") {
			steps {
				echo "Integration Test"
			}
		}post {
			always {
				echo " Superb!!!"
			}
		}
	}post {
		sucess {
			echo " I am Legend!!! I run always"
		}
		failure {
			echo " Tunr on the Bat signal..."
		}	
		always {
			echo " Jai Dinkan"
		}
	}
}
