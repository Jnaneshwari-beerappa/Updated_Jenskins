pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the project using Maven."
                // Maven commands to build the project
            }
            tools {
                maven 'Maven 3.6.3'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests with JUnit and integration tests with Selenium."
                // Commands for JUnit and Selenium would go here
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube."
                // SonarQube analysis commands here
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Conducting security scan with OWASP ZAP."
                // OWASP ZAP security scan commands here
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 staging environment."
                // AWS CLI commands for deployment to staging
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in the staging environment."
                // Commands for running integration tests on staging
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 production server."
                // AWS CLI commands for deployment to production
            }
        }
    }
    
    post {
        success {
            emailext (
                recipients: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Success",
                body: "The pipeline completed successfully.",
                attachmentsPattern: '**/build-outputs/**/*.log'  // Match log files in build-outputs directories
            )
        }
        failure {
            emailext (
                recipients: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Failure",
                body: "The pipeline failed. Please check the logs.",
                attachmentsPattern: '**/build-outputs/**/*.log'  // Match log files in build-outputs directories
            )
        }
    }
}
