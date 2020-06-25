pipeline{

	agent any

	stages{

		stage("Git Clone"){
		steps{
			git credentialsId: 'ci-cd-repo-credentials', \
			 url: 'https://github.com/AhmedAtefGaber/spree'
				}
		                        }
		stage("requirements"){
		steps{
			sh 'gem install bundler -v 2.1.4 '	
			}
					}
		stage("Docker Build"){
		steps{
			sh "docker build  -t ahmedatefosman/spree ."
			}
				}
		stage("Docker Push"){
		steps{	
			withCredentials([string(credentialsId: 'docker_pass', \
                                                        variable: 'docker_pass')]) {
			sh "docker login -u ahmedatefosman -p ${docker_pass} "
					}
			sh "docker push ahmedatefosman/spree"
			
			}
				}
		stage("Deploy on kubernetes as deplyment and access the app from the service"){
		steps{
			sh "kubectl apply -f k8s/"
		      }	
				}
		}
}
