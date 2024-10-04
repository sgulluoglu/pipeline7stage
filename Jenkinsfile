pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build the code using maven to compile and package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'JUnit for unit tests and Selenium for integration tests.'
                //sh 'fail-t' code to fail test step
            }
            post {
                always {
                    emailext(
                        to: "ssgulluoglu@gmail.com",
                        subject: "Jenkins: Unit and Integration Test ${currentBuild.result}",
                        body: "The unit and integration tests - ${currentBuild.result} . Please check the logs for more details.",
                        attachLog: true,
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code quality analysis using SonarQube.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Perform a security scan using Fortify.'
                //sh 'fail-s' code to fail security scan step
            }
            post {
                always {
                    emailext(
                        to: "ssgulluoglu@gmail.com",
                        subject: "Jenkins: Security Scan ${currentBuild.result}",
                        body: "Fortify scan - ${currentBuild.result}. Please check the logs for the result.",
                        attachLog: true,
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploy the application to a staging server on AWS EC2.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Integration tests on the staging environment using Selenium.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploy the application to a production server on AWS EC2.'
            }
        }
    }
}