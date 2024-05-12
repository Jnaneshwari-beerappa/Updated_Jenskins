          // Stage 1: Build
echo 'Starting the Build process using Maven.'
// Assuming you're using a shell script or Maven plugin in Jenkins:
sh 'mvn clean install'
echo 'Build completed.'

// Stage 2: Unit and Integration Tests
echo 'Running Unit and Integration Tests using JUnit and Selenium.'
sh 'mvn test' // This command will run tests assuming you have a Maven project.
echo 'Tests completed.'

// Email Notification with logs after testing
emailext (
    subject: 'CI Pipeline: Testing Stage Completed',
    body: 'The Testing stage has completed. Please find attached the logs for more details.',
    attachLog: true,
    recipient: 'jnaneshwarib63@gmail.com'
)

// Stage 3: Code Analysis
echo 'Analyzing code with SonarQube.'
sh 'mvn sonar:sonar' // Example Maven command for SonarQube
echo 'Code analysis completed.'

// Stage 4: Security Scan
echo 'Performing Security Scan using OWASP ZAP.'
// Example command to start the ZAP security scan
sh 'zap-cli start'
sh 'zap-cli scan --recursive http://your-staging-url.com'
echo 'Security scan completed.'

// Email Notification with logs after security scan
emailext (
    subject: 'CI Pipeline: Security Scan Stage Completed',
    body: 'The Security Scan stage has completed. Please find attached the logs for more details.',
    attachLog: true,
    recipient: 'jnaneshwarib63@gmail.com'
)

// Stage 5: Deploy to Staging
echo 'Deploying application to staging environment.'
// Deployment command or script
sh 'deploy-to-staging.sh'
echo 'Deployment to staging completed.'

// Stage 6: Integration Tests on Staging
echo 'Running Integration Tests on the staging environment.'
// Running tests on staging, for example using Selenium
sh 'run-staging-tests.sh'
echo 'Integration tests on staging completed.'

// Stage 7: Deploy to Production
echo 'Deploying application to production environment.'
// Deployment command or script
sh 'deploy-to-production.sh'
echo 'Deployment to production completed.'

// Final Notification
emailext (
    subject: 'CI Pipeline: Production Deployment Completed',
    body: 'The application has been successfully deployed to production.',
    attachLog: true,
    recipient: 'jnaneshwarib63@gmail.com'
)
