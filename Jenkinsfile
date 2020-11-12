pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/dunglt42/hello-world.git'
            }
        }
		stage('Build') {
			steps {
				withDockerRegistry(credentialsId: 'aws-docker-hub', url: 'https://index.docker.io/v1/') {
				sh 'docker build -t dunglt42/hello-world:v1 .'
				sh 'docker push dunglt42/hello-world:v1'
				sh 'docker run -d --name hello_world_cont -p 81:80 dunglt42/hello-world:v1'
				}
			}
		}		
    }
}
