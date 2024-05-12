pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting the Build process using Maven.'
                echo 'Build completed.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests using JUnit and Selenium.'
                echo 'Tests completed.'
            }
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Testing Stage Completed',
                        body: 'The Testing stage has completed. Please find attached the logs for more details.',
                        attachLog: true,
                        attachmentsPattern: '**/target/surefire-reports/*.xml', // Example for JUnit test reports
                        to: 'jnaneshwarib63@gmail.com'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube.'
                echo 'Code analysis completed.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP ZAP.'
                echo 'Security scan completed.'
            }
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Security Scan Stage Completed',
                        body: 'The Security Scan stage has completed. Please find attached the logs for more details.',
                        attachLog: true,
                        attachmentsPattern: '**/zap-reports/*.html', // Example for OWASP ZAP security reports
                        to: 'jnaneshwarib63@gmail.com'
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging environment.'
                echo 'Deployment to staging completed.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on the staging environment.'
                echo 'Integration tests on staging completed.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production environment.'
                echo 'Deployment to production completed.'
            }
            post {
                always {
                    emailext(
                        subject: 'CI Pipeline: Production Deployment Completed',
                        body: 'The application has been successfully deployed to production. Attached are the deployment logs.',
                        attachLog: true,
                        attachmentsPattern: '**/logs/deployment.log', // Example for deployment logs
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
                attachmentsPattern: '**/logs/errorLogs.log', // Example for general error logs
                to: 'jnaneshwarib63@gmail.com'
            )
        }
    }
}
