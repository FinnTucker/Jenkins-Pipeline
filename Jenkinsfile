pipeline{
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Building the project... A tool such as Maven can be used to compile the source code, resolve dependencies and package the application."
            }  
        }

        stage("Unit and Integration Tests"){
            steps{
                echo "JUnit can be used for unit testing to ensure that individual coomponents work correctly, and TestNG can be used for integration testing to verify that different components work together."
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
                echo "analyse code to ensure it meets industry standards. SonarQube is a powerful tool for the continuous inspection of the quality of code. It analyses for bugs, vulnerabilities, code smells and technical debt. It provides actionable insights and maintains high quality standards for code."
            }
        }
        stage("Security Scan"){
            steps{
                echo "Scan for security vulnerabilities. Snyk is a popular tool for detecting and fixing vulnerabilities in source code, dependencies, container images and infrastructure configuration files."
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
                echo "Deploy the application to a staging server (eg Amazon Elastic Compute Cloud). The production environment is a near-identical EC2 instance, it can be created from the identical AMI (Amazon Machine Image)"
            }
        }
        stage("Integration tests on Staging Platform"){
            steps{
                echo "Run integration tests on staging environment to ensure it runs as expected in a production-like environment"
            }
            post{
                success{
                    emailext(
                        subject:"staging platform integration test Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """The staging platform integration test for ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.
                                Check out the console output at ${env.BUILD_URL}">${env.BUILD_URL}consoleText to view the results.""",
                        to: "finn.jgt1996@gmail.com",
                        attachLog: true                        
                    )
                }
                failure{
                    emailext(
                        subject:"staging platform integration test failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
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


