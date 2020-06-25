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
		
		}

}
