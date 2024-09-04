pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                echo 'Task: Compile and package the code using a build automation tool.'
                echo 'Tool: Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
                echo 'Task: Run unit tests to ensure code functions as expected, and integration tests to check if different components work together.'
                echo 'Tools: JUnit for unit tests, Selenium for integration tests'
            }
            post {
                success {
                    echo "Attempting to send success email for Unit and Integration Tests..."
                    try {
                        emailext(
                            to: 'biniltomjose12780@gmail.com',
                            subject: "Jenkins Pipeline: Unit and Integration Tests - SUCCESS",
                            body: "The Unit and Integration Tests stage has completed successfully. Please find the logs attached.",
                            attachLog: true,
                            debug: true
                        )
                        echo "Email sent successfully for Unit and Integration Tests"
                    } catch (Exception e) {
                        echo "Failed to send email for Unit and Integration Tests: ${e}"
                    }
                    // Add a sleep to avoid email rate-limiting issues
                    sleep time: 5, unit: 'SECONDS'
                }
                failure {
                    echo "Attempting to send failure email for Unit and Integration Tests..."
                    try {
                        emailext(
                            to: 'biniltomjose12780@gmail.com',
                            subject: "Jenkins Pipeline: Unit and Integration Tests - FAILURE",
                            body: "The Unit and Integration Tests stage has failed. Please find the logs attached.",
                            attachLog: true,
                            debug: true
                        )
                        echo "Failure email sent successfully for Unit and Integration Tests"
                    } catch (Exception e) {
                        echo "Failed to send failure email for Unit and Integration Tests: ${e}"
                    }
                    sleep time: 5, unit: 'SECONDS'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
                echo 'Task: Analyze code quality to ensure it meets industry standards.'
                echo 'Tool: SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
                echo 'Task: Perform a security scan to identify vulnerabilities in the code.'
                echo 'Tool: OWASP Dependency-Check'
            }
            post {
                success {
                    echo "Attempting to send success email for Security Scan..."
                    try {
                        emailext(
                            to: 'biniltomjose12780@gmail.com',
                            subject: "Jenkins Pipeline: Security Scan - SUCCESS",
                            body: "The Security Scan stage has completed successfully. Please find the logs attached.",
                            attachLog: true,
                            debug: true
                        )
                        echo "Email sent successfully for Security Scan"
                    } catch (Exception e) {
                        echo "Failed to send email for Security Scan: ${e}"
                    }
                    sleep time: 5, unit: 'SECONDS'
                }
                failure {
                    echo "Attempting to send failure email for Security Scan..."
                    try {
                        emailext(
                            to: 'biniltomjose12780@gmail.com',
                            subject: "Jenkins Pipeline: Security Scan - FAILURE",
                            body: "The Security Scan stage has failed. Please find the logs attached.",
                            attachLog: true,
                            debug: true
                        )
                        echo "Failure email sent successfully for Security Scan"
                    } catch (Exception e) {
                        echo "Failed to send failure email for Security Scan: ${e}"
                    }
                    sleep time: 5, unit: 'SECONDS'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
                echo 'Task: Deploy the application to a staging server for further testing.'
                echo 'Tool: AWS CLI'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
                echo 'Task: Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment.'
                echo 'Tool: Postman for API testing, Selenium for UI testing'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
                echo 'Task: Deploy the application to the production environment.'
                echo 'Tool: AWS CLI'
            }
        }
    }

    post {
        success {
            echo "Sending global success email..."
            mail to: 'biniltomjose12780@gmail.com',
                 subject: "Jenkins Pipeline completed successfully",
                 body: "The entire pipeline has completed successfully."
        }
        failure {
            echo "Sending global failure email..."
            mail to: 'biniltomjose12780@gmail.com',
                 subject: "Jenkins Pipeline failed",
                 body: "The pipeline has encountered a failure."
        }
    }
}
