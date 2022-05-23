pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        //dockerImage = ''
	docker_id = credentials('DOCKER_ID')
        docker_cred = credentials('DOCKER_PASSWORD')
        def customImage = ''
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
			    sh 'docker login -u $docker_id -p $docker_cred'
			    echo "${docker_id}"
			    customImage = docker.build "my-image:${BUILD_NUMBER}"
			   //def dockerImage = sh 'docker build -t  $registry:$BUILD_NUMBER .'   
			    echo "$customImage"
		    }
                }
          }
        stage('Deploy') {
            steps {
		    script {    
			    //echo "${registryCredential}"
			    docker.withRegistry( '', registryCredential ) {
			    dockerImage.push("$BUILD_NUMBER")
               		//sh 'docker push $dockerImage '
		    }
            }
        }
    }	    
  }
}
