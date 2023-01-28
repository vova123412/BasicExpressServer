pipeline {
    agent any
    tools {nodejs "node"}
    environment {
        NEW_VERSION ='1.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }

    stages {
        stage('Build') {
            steps {
                git branch: 'basicserver', url: 'https://github.com/vova123412/BasicExpressServer.git'
                bat "npm install"
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
