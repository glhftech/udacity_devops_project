pipeline {
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
					dockerImage.push()
					}
				}
			}
		}
	
}
}