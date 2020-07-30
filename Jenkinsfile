pipeline {
  agent any 
  stages {
	 stage('Lint') {
		  steps {
			  sh 'echo "Hello World 111"'
		  }
	 }  
	 stage('Docker build') {
			  docker.build("glhftech/myapp")
		  }
	 }
  }
