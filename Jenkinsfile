
pipeline {
    agent any
    environmet {
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
            when {
                expression {
                    BRANCH_NAME == 'basicserver'
                }
                echo "building version ${NEW_VERSION}"
                
                }
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                withCredentials([
                    usernamePassword(credentails: 'server-credentials',usernameVaiable: USER, passwordVariable: PWD)
                ])
                echo "deploying with ${SERVER_CREDENTIALS}"
                sh "some script ${USER} ${PWD}" 
            }
        }
    }
    post {
        always {
            // always do this no metter what success or fail
        }
        success{
            echo " sucess"
        }
        failure {
            echo "failed"
        }
    }
}
