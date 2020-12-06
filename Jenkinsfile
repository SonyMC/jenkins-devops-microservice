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
		}
		stage("Test") {
			steps {
				echo " Test"
			}
		}
		stage("Integration Test") {
			steps {
				echo "Integration Test"
			}
		}
	}
	post {
		success {
			echo " I am Legend!!! I run always"
		}
		failure {
			echo " Turn on the Bat signal..."
		}
		unstable {
			echo " Whoa..earhquake...unstable..."
		}	
		notBuilt {
			echo " Give me red...unbuilt..."
		}		
		always {
			echo " Jai Dinkan"
		}
	}
}
