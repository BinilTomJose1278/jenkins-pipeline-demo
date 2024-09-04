pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven..."
                // Example: sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running Unit and Integration Tests using JUnit..."
                // Example: sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code quality using SonarQube..."
                // Example: sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP Dependency-Check..."
                // Example: sh 'dependency-check.sh --project myapp --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to Staging environment (e.g., AWS EC2)..."
                // Example: sh 'deploy-to-staging.sh'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running Integration Tests on Staging environment..."
                // Example: sh 'run-integration-tests.sh'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying application to Production environment (e.g., AWS EC2)..."
                // Example: sh 'deploy-to-production.sh'
            }
        }
    }

    post {
        always {
            mail to: "biniltomjose12780@gmail.com",
                 subject: "Build and Test Pipeline - Status",
                 body: "The pipeline has completed. Check the logs for details.",
                 attachLog: true
        }
        success {
            echo "Pipeline completed successfully."
        }
        failure {
            echo "Pipeline failed. Check logs for details."
        }
    }
}
