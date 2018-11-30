pipeline{
   agent any
    stages 
	{
		stage("build"){
			steps{
				sh """go build main.go"""
			}
		}
		stage("docker build"){
			steps{
				sh """docker build -t mygo ."""
			}
		}
		stage("push"){
			steps{
				echo "push"		
		}
		}
	}
}
