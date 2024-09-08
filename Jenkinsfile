pipeline {
    agent any
    stages {
        stage('Test Email') {
            steps {
                echo 'Testing email sending...'
                emailext(
                    to: 'ssgulluoglu@gmail.com',
                    subject: 'Jenkins Test Email',
                    body: 'This is a test email from Jenkins.',
                    attachLog: true
                )
            }
        }
    }
}
