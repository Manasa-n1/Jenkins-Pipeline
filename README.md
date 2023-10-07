# Jenkins-Pipeline
pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = "/path/to/code/directory"
        TESTING_ENVIRONMENT = "test environment"
        PRODUCTION_ENVIRONMENT = "production environment"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path: ${env.DIRECTORY_PATH}"
                echo "compile the code and generate any necessary artifacts."
            }
        }
        
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying the application to the testing environment: ${env.TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Approval') {
            steps {
                script {
                    echo "Waiting for manual approval"
                    sleep 10
                    echo "Manual approval done"
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
