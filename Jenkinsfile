// Declarative script - > Does not require a node like a Scripted script
// Instead of keyword Node we use Pipeline
// Stages , stage and steps are mandatory for a declarative script
pipeline{
	// agent is where the build is going to run
	agent any
	//agent { docker { image 'maven:3.6.3' } }  // using a docker image with maven installation  
	//agent { docker { image 'node:15.3' } }  // using a docker image with node installation 
	// The following environment extraction picks up the home folder location for Docker and Maven and sets the PATH. We use the names as specified in the Jnekins cosole via  manage Jenkins -> Global Tool Configuration
	environment{
		dockerHome = tool 'myDocker' // This is the Docker name we have in the Jenkins UI console -> Manage Jenkins -> Global Tool Configuration
		mavenHome  = tool 'myMaven' // This is the Maven name we have in the Jenkins UI console -> Manage Jenkins -> Global Tool Configuration
		//PATH = "$dockerHome/bin:$PATH"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage("Build") {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "Path : $PATH"
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
