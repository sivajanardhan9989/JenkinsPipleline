 pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'HOURS')

    }

    environment { 
        CC = 'sivajanardhan'
    }

    stages {
        stage('Build') {
            
            steps {
                echo "Building the apps and "
             sh '''
                ls -ltr 
                pwd 
                echo "Hello from github webhook"
              '''

            }
        }
    
        stage('Example') {
            
            steps {
                sh 'printenv'
            }

        }
        stage('Test') {
            steps {
                echo "Testing the app"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the app"
            }
        }

    }

    post {
        always {
            echo "This will always run"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
        unstable {
            echo "This will run only if the run was unstable"
        }
        changed {
            echo "This will run only if the state of the Pipeline has changed"
            echo "For example, if the Pipeline was previously failing but is now successful"
        }
    }
}

 
