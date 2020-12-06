// Declarative script - > Does not require a node like a Scripted script
// Instead of keyword Node we use Pipeline
// Stages , stage and steps are mandatory for a declarative script
pipeline{
	// agent is where the build is going to run
	agent any
	//agent { docker { image 'maven:3.6.3' } }  // using a docker image with maven installation  
	//agent { docker { image 'node:15.3' } }  // using a docker image with node installation 
	stages {
		stage("Build") {
			steps {
				// sh 'mvn --version'
				// sh 'node --version'
				echo "Build"
				echo "Pathe : $PATH"
				echo "BUILD_NUMBER : $env.BUILD_NUMBER"
				echo "BUILD_ID : $env.BUILD_ID"
				echo "JOB_NAME : $env.JOB_NAME"
				echo "BUILD_TAG : $env.BUILD_TAG"
				echo "BUILD_URL: $env.BUILD_URL"
				echo "JOB_URL: $env.JOB_URL"
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
		changed {
			echo " If you want change you must bring change - Conductor Vasu"
		}		
		always {
			echo " Jai Dinkan"
		}
	}
}
