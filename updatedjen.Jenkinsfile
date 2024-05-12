pipeline {
    agent any
    environment {
        LOG_DIR = "${WORKSPACE}/logs"  // Sets the directory for logs within the Jenkins workspace
    }
    stages {
        stage('Prepare') {
            steps {
                echo "Preparing the environment..."
                sh "mkdir -p ${LOG_DIR}"  // Creates the log directory
            }
        }
        stage('Build') {
            steps {
                echo "Building the project using Maven..."
                script {
                    sh "mvn clean package > ${LOG_DIR}/build.log"  // Building the project with Maven and logging the output
                }
                archiveArtifacts artifacts: "${LOG_DIR}/build.log", onlyIfSuccessful: true
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests..."
                script {
                    sh "mvn test > ${LOG_DIR}/test.log"  // Running tests using Maven and logging the output
                }
                archiveArtifacts artifacts: "${LOG_DIR}/test.log", onlyIfSuccessful: true
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube..."
                script {
                    sh "mvn sonar:sonar > ${LOG_DIR}/sonar.log"  // Integrating SonarQube for code quality checks
                }
                archiveArtifacts artifacts: "${LOG_DIR}/sonar.log", onlyIfSuccessful: true
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan..."
                script {
                    // Example command; replace with your actual security scan command
                    sh "./security-scan.sh > ${LOG_DIR}/security.log"
                }
                archiveArtifacts artifacts: "${LOG_DIR}/security.log", onlyIfSuccessful: true
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to staging environment..."
                script {
                    // Example AWS CLI command to deploy; replace with your actual deployment script
                    sh "aws s3 cp target/myapp.war s3://my-staging-bucket/myapp.war"
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in staging environment..."
                script {
                    // Example integration testing command; replace with your actual test command
                    sh "curl -s http://staging.myapp.com/health > ${LOG_DIR}/staging-test.log"
                }
                archiveArtifacts artifacts: "${LOG_DIR}/staging-test.log", onlyIfSuccessful: true
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying application to production environment..."
                script {
                    // Example AWS CLI command to deploy; replace with your actual deployment script
                    sh "aws s3 cp s3://my-staging-bucket/myapp.war s3://my-production-bucket/myapp.war"
                }
            }
        }
    }
    post {
        success {
            emailext(
                recipients: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Success",
                body: "The pipeline completed successfully. See attached logs for more details.",
                attachmentsPattern: "${LOG_DIR}/*.log"
            )
        }
        failure {
            emailext(
                recipients: 'jnaneshwarib63@gmail.com',
                subject: "Pipeline Failure",
                body: "The pipeline failed. Please see the attached logs for more details.",
                attachmentsPattern: "${LOG_DIR}/*.log"
            )
        }
    }
}
