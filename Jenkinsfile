pipeline {
    agent any
    environment {
        NEW_VERSION ='1.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                 echo "building version ${NEW_VERSION} after expression"
                 echo 'Testing...'
                }
            }
        
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                echo "deploying with ${SERVER_CREDENTIALS}"
                bat "docker ps -all" 
            }
        }
    }
    post {
        always  {
             echo "Cleaning up resources"
        }
        success{
            echo " sucess"
        }
        failure {
            echo "failed"
        }
    }
}
