pipeline {
  agent any 
  stages {
	 stage('Lint') {
		  steps {
			  sh 'echo "Hello World 111"'
		  }
	 }  
	 
	 stage('Docker build') {
		steps{
			script {
				dockerImage = docker.build("glhftech/myapp")
			}
  	}
	}
}
}