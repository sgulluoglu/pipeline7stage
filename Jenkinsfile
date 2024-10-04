    post {
         always {
             echo 'This will always run'
         }
         success {
             echo 'This will run only if successful'
         }
         failure {
             echo 'This will run only if Pipeline Failed'
             // Sending an email notification with details about the failure
             mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: 'ganesh_1@mail.com', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "ganesh_2@mail.com";
         }
         unstable {
             echo 'This will run only if the run was marked as unstable'
         }
     }
