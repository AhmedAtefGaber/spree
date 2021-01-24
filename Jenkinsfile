pipeline{

	agent { 
        docker { image "node2:5000/spree-jenkins-agent" 
                 args '-v /var/run/docker.sock:/var/run/docker.sock -v /etc/hosts:/etc/hosts  -v /home/devops/.kube/config:/home/agent/.kube/config'   
        	}
   		}

	stages{
		stage("Docker Build"){
			steps{
				sh "docker build  -t node2:5000/spree ."
			}
		}
		stage("Docker Push"){
			steps{	
				sh "docker push node2:5000/spree"
				
			}
		}
		stage("Deploy to kubernetes"){
			steps{
				sh "kubectl apply -f k8s/"
			}	
		}
	}
}
