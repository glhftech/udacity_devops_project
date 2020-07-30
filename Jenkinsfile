pipeline {
  agent any 
  stages {
	 stage('Lint') {
		  steps {
			  sh 'echo "Hello World 111"'
		  }
	 }  
	 stage('Docker build') {
		  steps {
			  docker.build("glhftech/myapp")
			  }
		  }
	 }
  }
