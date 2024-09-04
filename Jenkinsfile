pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                echo 'Task: Compiling and packaging the code using Maven.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
                echo 'Task: Running unit tests to verify functionality and integration tests to ensure components work together.'
                echo 'Tools: JUnit for unit tests, Selenium for integration tests'
            }
            post {
                success {
                    emailext(
                        to: 'biniltomjose12780@gmail.com',
                        subject: "Build Success: Unit and Integration Tests Passed",
                        body: """
                        Hello,

                        The Unit and Integration Tests stage in your Jenkins pipeline has passed successfully.
                        
                        Stage: Unit and Integration Tests
                        Status: SUCCESS

                        You can review the logs attached to this email for more details.

                        Best regards,
                        Jenkins
                        """,
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'biniltomjose12780@gmail.com',
                        subject: "Build Failure: Unit and Integration Tests Failed",
                        body: """
                        Hello,

                        Unfortunately, the Unit and Integration Tests stage in your Jenkins pipeline has failed.
                        
                        Stage: Unit and Integration Tests
                        Status: FAILURE

                        Please review the logs attached to this email for further details on the failure.

                        Regards,
                        Jenkins
                        """,
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
                echo 'Task: Analyzing code quality and ensuring it adheres to industry standards using SonarQube.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
                echo 'Task: Performing a security scan to identify vulnerabilities in the code using OWASP Dependency-Check.'
            }
            post {
                success {
                    emailext(
                        to: 'biniltomjose12780@gmail.com',
                        subject: "Build Success: Security Scan Passed",
                        body: """
                        Hello,

                        The Security Scan stage in your Jenkins pipeline has completed successfully.
                        
                        Stage: Security Scan
                        Status: SUCCESS

                        Please find the attached logs for further information.

                        Best regards,
                        Jenkins
                        """,
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'biniltomjose12780@gmail.com',
                        subject: "Build Failure: Security Scan Failed",
                        body: """
                        Hello,

                        The Security Scan stage in your Jenkins pipeline has failed.
                        
                        Stage: Security Scan
                        Status: FAILURE

                        Check the attached logs for more information on the issues.

                        Regards,
                        Jenkins
                        """,
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
                echo 'Task: Deploying the application to a staging server for further testing using AWS CLI.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
                echo 'Task: Running integration tests on the staging environment to ensure functionality in a production-like setting.'
                echo 'Tools: Postman for API testing, Selenium for UI testing'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
                echo 'Task: Deploying the application to the production environment using AWS CLI.'
            }
        }
    }

    post {
        success {
            mail to: 'biniltomjose12780@gmail.com',
                 subject: "Pipeline Success: Jenkins Pipeline Completed Successfully",
                 body: """
                 Hello,

                 The entire Jenkins pipeline has completed successfully.

                 Pipeline Status: SUCCESS

                 All stages passed, and the application has been successfully deployed.

                 Best regards,
                 Jenkins
                 """
        }
        failure {
            mail to: 'biniltomjose12780@gmail.com',
                 subject: "Pipeline Failure: Jenkins Pipeline Encountered a Failure",
                 body: """
                 Hello,

                 The Jenkins pipeline has encountered a failure.

                 Pipeline Status: FAILURE

                 One or more stages failed during the execution. Please investigate the logs to identify the issue.

                 Regards,
                 Jenkins
                 """
        }
    }
}
