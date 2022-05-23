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
			sh 'docker login -u peruboinas -p snithi@123'
			dockerImage = docker.build ("peruboinas/testjenkinsdocker")	
                }
          }
        stage('Deploy') {
            steps {
                sh 'docker push peruboinas/testjenkinsdocker:latest'
            }
        }
    }	    
  }
