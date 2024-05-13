pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building using Maven..."
                // Maven could be invoked here
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running tests using JUnit and Selenium..."
                // JUnit and Selenium commands here
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube..."
                // SonarQube integration here
            }
        }
        stage('Security Scan') {
            steps {
                echo "Conducting security scan with OWASP ZAP..."
                // OWASP ZAP commands here
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 Staging..."
                // AWS CLI commands to deploy
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in staging environment..."
                // Testing commands here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 Production..."
                // AWS CLI commands to deploy
            }
        }
    }
    post {
        success {
            emailext to: 'jnaneshwarib63@gmail.com',
                     subject: "Pipeline Success",
                     body: "The pipeline completed successfully.",
                     attachLog: true
        }
        failure {
            emailext to: 'jnaneshwarib63@gmail.com',
                     subject: "Pipeline Failure",
                     body: "The pipeline failed. Please check the logs.",
                     attachLog: true
        }
    }
}
