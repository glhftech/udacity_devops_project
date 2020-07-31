pipeline {
	environment { 
	   VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
	}

  agent any 
  stages {
	 stage('Lint') {
		  steps {
			  sh 'hadolint Dockerfile'
		  }
	 }  
	 
	 stage('Docker build') {
		steps{
			script {
				dockerImage = docker.build("glhftech/myapp")
			}
  	}
	}
	
	stage('Push image') {
		steps{
			script {
				docker.withRegistry( '', 'dockerhub_id' ) {
					dockerImage.push("${env.BUILD_NUMBER}")
            		dockerImage.push("latest")
					}
				}
			}
		}
	
	stage('Cleaning up') {
		steps{
			sh "docker rmi glhftech/myapp:latest"
		}
	}

	
}
}