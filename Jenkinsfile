pipeline{
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Your build steps here
            }  
        }

        stage("Unit and Integration Tests"){
            steps{
                echo "Ensure code functions as expected and run integration tests to ensure application components work together"
            }
            post{
                success{
                    emailext(
                        subject:"unit and integration test Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The unit and integration test for ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true                        
                    )
                }
                failure{
                    emailext(
                        subject:"Unit and integration test failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The unit and integration test for ${env.JOB_NAME} #${env.BUILD_NUMBER} failed to complete.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true
                    )
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "analyse code to ensure it meets industry standards"
            }
        }
        stage("Security Scan"){
            steps{
                echo "Scan for security vulnerabilities"
            }
            post{
                success{
                    emailext(
                        subject:"Security scan Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The security scan for ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true                        
                    )
                }
                failure{
                    emailext(
                        subject:"security scan failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The security scan for ${env.JOB_NAME} #${env.BUILD_NUMBER} failed to complete.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true
                    )
                }
            }            
        }
        stage("Deploy To Staging"){
            steps{
                echo "Deploy the application to a staging server (eg Amazon Elastic Compute Cloud)"
            }
        }
        stage("Integration tests on Staging Platform"){
            steps{
                echo "Run integration tests on staging environment to ensure it runs as expected in a production-like environment"
            }
            post{
                success{
                    emailext(
                        subject:"Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The staging platform integration test for ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true                        
                    )
                }
                failure{
                    emailext(
                        subject:"Build failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The staging platform integration test for ${env.JOB_NAME} #${env.BUILD_NUMBER} failed to complete.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true
                    )
                }
            }            
        }
        stage("Deploy to Production"){
            steps{
                echo "deploy the application to production server (eg Production AWS EC2 instance)"
            }
        }
    }
}


