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
		dockerRegistry = "mailsonymathew/jenkins-currency-exchange-devops"  // we will use docker registry further down 
		registryCredential = 'dockerHub' //dockerHub is the name of the Docker credentails we have provided in the Jenkins UI -> Manage Jenkins -> Manage Credentials 
		dockerImage = ''
	}
	stages {
		stage("Checkout") {
			steps {
				echo "Build"
			// All environment variables can be found in Pipeline Syntax-> Global Variables reference	
				echo "Path : $PATH"
				echo "BUILD_NUMBER : $env.BUILD_NUMBER"
				echo "BUILD_ID : $env.BUILD_ID"
				echo "JOB_NAME : $env.JOB_NAME"
				echo "BUILD_TAG : $env.BUILD_TAG"
				echo "BUILD_URL: $env.BUILD_URL"
				echo "JOB_URL: $env.JOB_URL"
			}
		}
		stage("Compile"){
			steps{
				sh "mvn clean compile"
			}
		}
		stage("Test") {
			steps {
				sh "mvn test"
			}
		}
		stage("Integration Test") {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage("Package"){
			steps{
				sh "mvn package -DskipTests"  // We are skipping ruuning the tests again while buldign the package as it has already been run in the previosu steps.
			}

		}
		stage("Build Docker Image"){
			steps{
				script{
					//dockerImage = "docker build -t mailsonymathew/jenkins-currency-exchange-devops:$env.BUILD_TAG"
					 //dockerImage = docker.build("mailsonymathew/jenkins-currency-exchange-devops:${env.BUILD_TAG}")
					dockerImage = docker.build  dockerRegistry + ":${env.BUILD_TAG}"
				}
			}
		}
		stage("Push Docker Image"){
			steps{
				// "docker push mailsonymathew/jenkins-currency-exchange-devops:$env.BUILD_TAG"  -> This is an old method of doing this
				script{
// 					docker.withRegistry('','dockerHub'){  // add a wrapper providing docker credentails . dockerHub is the name of the Docker credentails we have provided in the Jenkins UI -> Manage Jenkins -> Maanage Credentials 
// 						dockerImage.push();
// 						dockerImage.push('latest') ; // add the latest tag to the docker Image.
					docker.withRegistry('',registryCredential){
						dockerImage.push()
					}
				}
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
			echo " Whoa..earthquake...unstable..."
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
