pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        dockerImage = ''
	docker_id = credentials('DOCKER_ID')
        docker_cred = credentials('DOCKER_PASSWORD')

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
			        sh('echo ${docker_id}')
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
