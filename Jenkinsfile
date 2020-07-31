pipeline {

    agent any

    stages {
        stage('Lint') {
            steps {
                sh 'hadolint Dockerfile'
            }
        }

        stage('Docker build') {
            steps {
                script {
                    dockerImage = docker.build("glhftech/myapp")
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub_id') {
                        dockerImage.push("${env.BUILD_NUMBER}")
                        dockerImage.push("latest")
                    }
                }
            }
        }

        stage('Cleaning up') {
            steps {
                sh "docker rmi glhftech/myapp:latest"
            }
        }

        stage('Rolling update deploy to k8s') {
            steps {
                sh "cat /home/ubuntu/deployment.yaml | sed 's/{{VERSION_NUM}}/${env.BUILD_NUMBER}/g' | kubectl apply -f -"
            }
        }

    }
}