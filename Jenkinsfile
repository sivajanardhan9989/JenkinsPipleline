 pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'HOURS')

    }

    environment { 
        CC = 'sivajanardhan'
    }


// triggers {
//         cron('*/2 * * * *')
//     }

    parameters {
        string(name: 'PERSON', defaultValue: 'SIVA', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

     

    stages {
      stage('inputs stage') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }

        stage('parameters') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }

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

 }