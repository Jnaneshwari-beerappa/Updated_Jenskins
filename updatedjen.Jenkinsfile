
              pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Assuming use of Maven for building
                    sh "mvn clean package > build.log"
                }
                archiveArtifacts artifacts: 'build.log', onlyIfSuccessful: true
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Assuming JUnit tests are run with Maven
                    sh "mvn test > test.log"
                }
                archiveArtifacts artifacts: 'test.log', onlyIfSuccessful: true
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    // Assuming SonarQube analysis
                    sh "mvn sonar:sonar > sonar.log"
                }
                archiveArtifacts artifacts: 'sonar.log', onlyIfSuccessful: true
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Assuming OWASP ZAP is used for security scanning
                    sh "./zap.sh > security.log"
                }
                archiveArtifacts artifacts: 'security.log', onlyIfSuccessful: true
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
            mail to: "jnaneshwarib63@gmail.com",
                subject: "Pipeline Success",
                body: "The pipeline completed successfully.",
                attachmentsPattern: '**/*.log'
        }
        failure {
            mail to: "jnaneshwarib63@gmail.com",
                subject: "Pipeline Failure",
                body: "The pipeline failed. Please check the logs.",
                attachmentsPattern: '**/*.log'
        }
    }
}
