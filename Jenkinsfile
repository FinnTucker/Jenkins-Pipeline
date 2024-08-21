pipeline {
    agent any

    stages {
        stage('Test Email') {
            steps {
                script {
                    emailext(
                        subject: "Test Email from Jenkins",
                        body: "This is a test email.",
                        to: "finn.jgt1996@gmail.com"
                    )
                }
            }
        }
    }
}
