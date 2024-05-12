pipeline {
    agent any
    environment {
        LOG_DIR = "${WORKSPACE}/logs"
    }
    stages {
        stage('Setup Log Directory') {
            steps {
                sh "mkdir -p ${LOG_DIR}"
            }
        }
        stage('Build') {
            steps {
                script {
                    sh "mvn clean package > ${LOG_DIR}/build.log 2>&1"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    sh "mvn test > ${LOG_DIR}/test_results.log 2>&1"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    sh "mvn sonar:sonar > ${LOG_DIR}/code_analysis.log 2>&1"
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    sh "mvn org.owasp:dependency-check-maven:check > ${LOG_DIR}/security_scan.log 2>&1"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Example deployment command
                    sh "echo 'Deploying to Staging Environment' > ${LOG_DIR}/staging_deploy.log 2>&1"
                    // Assume deployment commands here
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    sh "echo 'Running Integration Tests on Staging' > ${LOG_DIR}/staging_integration_tests.log 2>&1"
                    // Integration tests commands here
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    sh "echo 'Deploying to Production Environment' > ${LOG_DIR}/production_deploy.log 2>&1"
                    // Assume deployment commands here
                }
            }
        }
    }
    post {
        always {
            emailext (
                subject: "${JOB_NAME} ${BUILD_STATUS}: Build #${BUILD_NUMBER}",
                body: """<p>Build Completed - ${BUILD_STATUS}.</p>
                         <p>See attached logs for more details.</p>""",
                attachmentsPattern: "${LOG_DIR}/*.log",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
        success {
            emailext (
                to: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Success",
                body: "The pipeline completed successfully.",
                attachmentsPattern: "${LOG_DIR}/*.log"
            )
        }
        failure {
            emailext (
                to: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Failure",
                body: "The pipeline failed. Please check the logs.",
                attachmentsPattern: "${LOG_DIR}/*.log"
            )
        }
    }
}
