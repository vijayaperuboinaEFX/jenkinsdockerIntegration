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
				dockerImage = sh 'docker build -t  $registry:$BUILD_NUMBER .'
			        echo "$dockerImage"
		    }
                }
          }
        stage('Deploy') {
            steps {
                sh 'docker push "$dockerImage " '
            }
        }
    }	    
  }
