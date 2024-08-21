pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Building..."
            }
        }
        
        stage("Unit and Integration Tests"){
            steps{
                echo "Ensure code functions as expected and run integration tests to ensure application components work together"
            }
            post{
                success{
                    mail to: "finn.jgt1996@gmail.com",
                    subject: "Unit and Integration Test",
                    body: "Unit and integration test successful"
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
                success {
                    emailext(       
                        subject: "Security Scan for ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """<p>The security scan stage for <b>${env.JOB_NAME} #${env.BUILD_NUMBER}</b> completed successfully.</p>
                                 <p>Check out the console output at <a href="${env.BUILD_URL}consoleText">${env.BUILD_URL}consoleText</a> to view the results.</p>""",
                        attachLog: true,
                        to: "finn.jgt1996@gmail.com"
                        )
                    }
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
        }
        stage("Deploy to Production"){
            steps{
                echo "deploy the application to production server (eg Production AWS EC2 instance)"
            }
        }
    }


