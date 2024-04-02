pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "https://github.com/Sanchit-Gt/Task_6.2C/new/main"
        TESTING_ENVIRONMENT = "Sanchhit's Testing file "
        PRODUCTION_ENVIRONMENT = "Sanchit Gupta"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "Compiling the code and generating any necessary artifacts using mavin"
                  echo "update updated thhe file"
              
            }
        }
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests using Selenium"
            }
            post {
                success {
                    emailext  subject: 'Unit Test Status - Success', 
                              body: 'Unit Test has been completed successfully.', 
                              to: "sanchit2004gupta@gmail.com",
                              attachLog: true
                }
                failure {
                    emailext subject: 'Unit Test Status - Failure', 
                              body: 'Unit Test has failed.', 
                              to: "sanchit2004gupta@gmail.com",
                              attachLog: true
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code checkstyle"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan on the code using sync"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a testing environment using aws specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
            post {
                success {
                    emailext  subject: 'Security Scan Status - Success', 
                              body: 'Security Scan has been completed successfully.', 
                              to: "sanchit2004gupta@gmail.com",
                              attachLog: true
                }
                failure {
                    emailext subject: 'Security Scan Status - Failure', 
                              body: 'Security Scan has failed.', 
                              to: "sanchit2004gupta@gmail.com",
                              attachLog: true
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment using postman"
                
            }
        }
        stage('Approval') {
            steps {
                script {
                    echo "Pausing for manual approval...using jenkins"
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment using aws"
               
            }
        }
    }
}
