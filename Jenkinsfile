pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Tool: Maven
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Tools: JUnit, Selenium
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube...'
                // Tool: SonarQube
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Tool: OWASP ZAP
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // Tool: AWS CLI or Terraform
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running tests on staging environment...'
                // Tool: Postman
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                // Tool: AWS CLI or Terraform
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
        always {
            emailext (
                to: 'biniltomjose12780@gmail.com',
                subject: "Build ${currentBuild.fullDisplayName}",
                body: "Build ${currentBuild.fullDisplayName} completed with status: ${currentBuild.currentResult}",
                attachmentsPattern: '**/build.log'
            )
        }
    }
}
