pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
               echo 'build'
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
