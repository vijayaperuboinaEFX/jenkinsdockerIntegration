pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        dockerImage = ''
    }
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Cloning our Git') {
            steps {
                git 'https://github.com/vijayaperuboinaEFX/jenkinsdockerIntegration.git'
            }
          }   
	    stage('Building our image') {
            steps {
		    script {    
				sh 'docker login -u peruboinas -p snit@hi123'
				dockerImage = docker.build ("$registry" + ":$env.BUILD_NUMBER")
				}
                }
          }
        stage('Deploy') {
            steps {
                sh 'docker push peruboinas/testjenkinsdocker:latest'
            }
        }
    }	    
  }
