pipeline{
	agent any
	stages{
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
