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
				sh """
					EXPORT PATH=$PATH:/goroot/bin:/gopath/bin
					docker build -t mygo .
				"""
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