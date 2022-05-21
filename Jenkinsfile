pipeline { 
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
        stage('Test'){
            steps {
                 echo 'test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'make publish'
            }
        }
    }
}
