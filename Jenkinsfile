pipeline {
    environment {
        registry = 'peruboinas/testjenkinsdocker'
        registryCredential = 'docker-hub-credentials'
        //dockerSwarmManager = '10.40.1.26:2375'
        //dockerhost = '10.40.1.26'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning our Git') {
            steps {
                git 'https://github.com/vijayaperuboinaEFX/jenkinsdockerIntegration.git'
            }
        }
        stage('Building our image') {
            steps {
                 sh 'test2'
            }
        }
        
        stage('Push Image To DockerHUB') {
            steps {
               sh 'test3'
            }
        }
        stage('Cleaning up') {
            steps {
                sh 'cleaning'
            }
        }
        stage('Deploying to Docker Swarm') {
            steps {
                sh 'test4'
            }
        }
        stage('Verifying The Deployment') {
            steps {
                sh 'test5'
                }
        }
    }
}
