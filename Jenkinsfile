pipeline { 
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        //dockerSwarmManager = '10.40.1.26:2375'
        //dockerhost = '10.40.1.26'
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
                    dockerImage = docker.build("$registry:${env.BUILD_ID}")	
					sh'$dockerImage'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'make publish'
            }
        }
    }
}
