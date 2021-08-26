pipeline{
	agent { docker { image 'maven:3.6.3' } }
	stages{
		stage("Maven"){
			steps{
				script{
					docker.withRegistry('','dockerHub'){  // add a wrapper providing docker credentails . dockerHub is the name of the Docker credentails we have provided in the Jenkins UI -> Manage Jenkins -> Maanage Credentials 
				sh 'mvn --version'   // show the maven version when we use the agent for maven image 
			}
		}		
		stage('Build'){
			steps{
				echo "Build"
			}
		   }
		stage('Test'){
			steps{
				echo "Test"
			}
		   }
		stage('integration Test'){
			steps{
				echo "integration Test"
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
