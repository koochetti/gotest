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
		stage("push to DTR"){
			steps{
			withCredentials([usernamePassword(credentialsId: 'dp', usernameVariable: 'USER', passwordVariable: 'PASSWORD')])
			{
				sh """
					docker login --username $USER --password $PASSWORD
					docker push mygo
				"""
			}
		
		}
		}
	}
}