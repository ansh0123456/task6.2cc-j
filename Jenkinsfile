pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'react-app'
        DOCKER_CONTAINER = 'react-container'
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
        EMAIL_RECIPIENT = 'ansh4764.be23@chitkara.edu.in'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the React application...'
                echo 'Integration Steps: Install dependencies using npm, build the React app using Webpack or Vite, and generate optimized production assets.'
                echo 'What it does: Compiles React code into a minified, production-ready format.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Build Stage Completed',
                         body: 'React application build is complete.'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Integration Steps: Use Jest and React Testing Library to validate component functionality. Ensure test coverage meets project standards.'
                echo 'What it does: Tests individual React components and their integration with state and APIs.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Testing Stage Completed',
                         body: 'Unit and integration tests have been completed. Check logs for details.'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis with ESLint and SonarQube...'
                echo 'Integration Steps: Run ESLint to check code style and SonarQube for static code analysis.'
                echo 'What it does: Ensures the code follows best practices and detects potential bugs.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Code Analysis Completed',
                         body: 'Static code analysis is complete. Check SonarQube for reports.'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan with OWASP Dependency Check...'
                echo 'Integration Steps: Scan package dependencies for known vulnerabilities using OWASP Dependency Check.'
                echo 'What it does: Identifies security risks in project dependencies.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Security Scan Completed',
                         body: 'Security scanning has been completed. Review the report for details.'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying React app to staging using Docker...'
                echo 'Integration Steps: Build a Docker image with the React app, run an Nginx container to serve it, and expose it on the staging server.'
                echo 'What it does: Deploys the React app inside a Docker container, making it accessible for testing.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Staging Deployment Completed',
                         body: 'Deployment to the staging environment has finished. Validate the staging site.'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running end-to-end tests on staging with Selenium...'
                echo 'Integration Steps: Execute Selenium test cases against the staging URL to validate full application workflows.'
                echo 'What it does: Ensures that the deployed React app works correctly in the staging environment.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Integration Tests on Staging Completed',
                         body: 'Integration tests on the staging environment have been executed. Check Selenium reports for details.'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying React app to production using Docker...'
                echo 'Integration Steps: Build and tag the Docker image for production, push it to a registry (optional), and run an Nginx container to serve the React app.'
                echo 'What it does: Deploys the React app in a production-ready Docker container.'
            }
            post {
                always {
                    mail to: "${EMAIL_RECIPIENT}",
                         subject: 'Production Deployment Completed',
                         body: 'The React application has been successfully deployed to production. Check the live site for verification.'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
            echo 'Integration Steps: Ensure successful execution of all pipeline stages, from build to production deployment.'
            echo 'What it does: Confirms the React app is built, tested, analyzed, scanned, and deployed correctly.'
            mail to: "${EMAIL_RECIPIENT}",
                 subject: 'Pipeline Execution Successful',
                 body: 'The CI/CD pipeline for the React project has completed successfully.'
        }
        failure {
            echo 'Pipeline failed! Check the logs for more details.'
            echo 'Integration Steps: Identify the failing stage, analyze logs, and troubleshoot errors for resolution.'
            echo 'What it does: Notifies the team of pipeline failures for immediate attention.'
            mail to: "${EMAIL_RECIPIENT}",
                 subject: 'Pipeline Execution Failed',
                 body: 'The pipeline encountered an error. Review Jenkins logs for details.'
        }
    }
}

