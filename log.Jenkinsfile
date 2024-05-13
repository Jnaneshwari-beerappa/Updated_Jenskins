pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building using Maven..."
                // Maven could be invoked here
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Build Stage",
                        body: """<p>Build stage completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Running tests using JUnit and Selenium..."
                // JUnit and Selenium commands here
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Testing Stage",
                        body: """<p>Testing stage completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube..."
                // SonarQube integration here
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Code Analysis Stage",
                        body: """<p>Code Analysis stage completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo "Conducting security scan with OWASP ZAP..."
                // OWASP ZAP commands here
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Security Scan Stage",
                        body: """<p>Security Scan stage completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 Staging..."
                // AWS CLI commands to deploy
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Deployment to Staging Stage",
                        body: """<p>Deployment to Staging stage completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in staging environment..."
                // Testing commands here
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Integration Tests on Staging",
                        body: """<p>Integration Tests on Staging completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 Production..."
                // AWS CLI commands to deploy
            }
            post {
                always {
                    emailext (
                        to: 'jnaneshwarib63@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Deployment to Production",
                        body: """<p>Deployment to Production completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }
   
