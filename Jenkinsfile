pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        //dockerImage = ''
	docker_id = credentials('DOCKER_ID')
        docker_cred = credentials('DOCKER_PASSWORD')
        def customImage = ''
	def ImageName = ''
	registryUrl ='https://registry.hub.docker.com'
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
			    ImageName = "my-image:${BUILD_NUMBER}"
			    echo "$ImageName"
			    echo "$customImage"
			    
		    }
                }
          }
        stage('Deploy') {
            steps {
		    script {   
			    echo 'docker images ls'
			    docker.withRegistry("https://${registryUrl}", dockerRegistryCredentialsId) {
			    dockerImage.push("$BUILD_NUMBER")
               		    //sh 'docker push $dockerImage '
		    }
            }
        }
    }	    
  }
}
