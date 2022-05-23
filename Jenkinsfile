pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        dockerImage = ''
	DOCKER_ID = credentials('DOCKER_ID')
        DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')

    }
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Cloning our Git') {
            steps {
                git 'https://github.com/vijayaperuboinaEFX/jenkinsdockerIntegration.git'
		sh '$DOCKER_ID'     
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
		    script {    
				docker.withRegistry( '', registryCredential )    
               			 sh 'docker push $dockerImage '
		    }
            }
        }
    }	    
  }
