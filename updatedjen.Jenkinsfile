pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting the Build process using Maven.'
                
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests using JUnit and Selenium.'
                
            }
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Testing Stage Completed',
                        body: 'The Testing stage has completed. Please find attached the logs for more details.',
                        attachLog: true,
                        to: 'jnaneshwarib63@gmail.com'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube.'
                
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP ZAP.'
                
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Security Scan Stage Completed',
                        body: 'The Security Scan stage has completed. Please find attached the logs for more details.',
                        attachLog: true,
                        to: 'jnaneshwarib63@gmail.com'
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging environment.'
                
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on the staging environment.'
                
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production environment.'
               
            }
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Production Deployment Completed',
                        body: 'The application has been successfully deployed to production.',
                        attachLog: true,
                        to: 'jnaneshwarib63@gmail.com'
                    )
                }
            }
        }
    }
    post {
        failure {
            emailext(
                subject: 'CI Pipeline: Failure Alert',
                body: 'One or more stages in the pipeline have failed. Please check the Jenkins logs for more details.',
                attachLog: true,
                to: 'jnaneshwarib63@gmail.com'
            )
        }
    }
}
