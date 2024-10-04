pipeline 
{ 
    agent any

    options {
        timestamps() // Adds timestamps to console output -
        buildDiscarder(logRotator(daysToKeepStr: '30', numToKeepStr: '5')) // Discards old builds
    }

    environment {
        EMAIL_TO = 'ssgulluoglu@gmail.com' // The recipient for the email notification
    }

    stages {

        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven...'
                // Simulate Maven build --
                echo 'Simulating: mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Running Unit and Integration Tests...'
                // Simulate running JUnit tests
                echo 'Simulating: mvn test' // Simulate JUnit tests

                script {
                    def testStatus = 'success' // Change to "failure" to simulate a failed test
                    if (testStatus == 'success') {
                        echo 'Unit and Integration Tests passed successfully.'
                        emailext(
                            to: "${EMAIL_TO}",
                            subject: "Jenkins: Unit and Integration Test Success",
                            body: "The unit and integration tests passed successfully. Please check the logs for more details.",
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    } else {
                        echo 'Unit and Integration Tests failed.'
                        emailext(
                            to: "${EMAIL_TO}",
                            subject: "Jenkins: Unit and Integration Test Failure",
                            body: "The unit and integration tests failed. Please check the logs for more details.",
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Running static code analysis using SonarQube...'
                echo 'Simulating: sonar-scanner -Dsonar.projectKey=your_project_key -Dsonar.sources=./src'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Running OWASP ZAP scan...'
                script {
                    def securityScanStatus = 'success' // Change to "failure" to simulate a failed scan
                    if (securityScanStatus == 'success') {
                        echo 'Security Scan passed successfully.'
                        emailext(
                            to: "${EMAIL_TO}",
                            subject: "Jenkins: Security Scan Success",
                            body: "The security scan passed successfully. Please check the logs for more details.",
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    } else {
                        echo 'Security Scan failed.'
                        emailext(
                            to: "${EMAIL_TO}",
                            subject: "Jenkins: Security Scan Failure",
                            body: "The security scan failed. Please check the logs for more details.",
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying to AWS EC2 Staging...'
                echo 'Simulating: Deploying application to staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging...'
                script {
                    def stagingTestStatus = 'success' // Change to "failure" to simulate a failed test
                    if (stagingTestStatus == 'success') {
                        echo 'Integration Tests on Staging passed successfully.'
                    } else {
                        echo 'Integration Tests on Staging failed.'
                    }
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying to AWS EC2 Production...'
                echo 'Simulating: Deploying application to production server'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}
