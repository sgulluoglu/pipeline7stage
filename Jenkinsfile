pipeline {
    agent any

    environment {
        EMAIL = 'ssgulluoglu@gmail.com'
    }

    options {
        // Wait for 60 seconds before starting the job after a commit is detected
        disableConcurrentBuilds() // Avoid running concurrent jobs
        quietPeriod(60) // Delay the job execution by 60 seconds 
    }

    triggers {
        // Automatically trigger the pipeline on changes to the GitHub repository
        pollSCM('H/2 * * * *') // Poll the repository every 2 minutes for new commits (configured on Jenkins )
    }

    stages {

        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven...'
                // Simulate Maven build
                echo 'mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running tests using JUnit and Selenium...'
                script {
                    def testStatus = 'success' // Change to 'failure' to simulate failure
                    if (testStatus == 'success') {
                        echo 'Unit and Integration Tests passed successfully.'
                        emailext subject: 'Unit and Integration Tests Success',
                                 to: "${EMAIL}",
                                 body: "The Unit and Integration Tests stage was successful."
                    } else {
                        echo 'Unit and Integration Tests failed.'
                        emailext subject: 'Unit and Integration Tests Failure',
                                 to: "${EMAIL}",
                                 body: "The Unit and Integration Tests stage failed."
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Running static code analysis using SonarQube with Selenium code...'
                // Simulate SonarQube analysis
                echo 'sonar-scanner -Dsonar.projectKey=your_project_key -Dsonar.sources=./src -Dsonar.tests=./test -Dsonar.java.binaries=./target/classes'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Scanning code for vulnerabilities using OWASP ZAP...'
                script {
                    def securityScanStatus = 'success' // Change to 'failure' to simulate failure
                    if (securityScanStatus == 'success') {
                        echo 'Security Scan passed successfully.'
                        emailext subject: 'Security Scan Success',
                                 to: "${EMAIL}",
                                 body: "The Security Scan stage was successful."
                    } else {
                        echo 'Security Scan failed.'
                        emailext subject: 'Security Scan Failure',
                                 to: "${EMAIL}",
                                 body: "The Security Scan stage failed."
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to AWS EC2 Staging instance...'
                // Simulate deployment
                echo 'Deploying to AWS EC2 Staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests in the staging environment...'
                // Simulate integration tests
                script {
                    def stagingTestStatus = 'success' // Change to 'failure' to simulate failure
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
                echo 'Stage 7: Deploy to Production - Deploying the application to AWS EC2 Production instance...'
                // Simulate deployment
                echo 'Deploying to AWS EC2 Production'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}
