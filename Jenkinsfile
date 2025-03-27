pipeline {
    agent any
    
    environment {
        EMAIL_RECIPIENT = 'ansh4764.be23@chitkara.edu.in'
        USER_EMAIL = 'ansh4764.be23@chitkara.edu.in'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application using Maven...'
                sh 'mvn clean package'  // Maven: A build automation tool for Java projects
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Build Stage Completed',
                         body: 'The build stage has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit...'
                sh 'mvn test'  // JUnit: A framework for writing and running unit tests in Java
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Unit and Integration Tests Completed',
                         body: 'The unit and integration tests have completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis using SonarQube...'
                sh 'mvn sonar:sonar'  // SonarQube: A tool for continuous code quality inspection
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Code Analysis Completed',
                         body: 'The code analysis stage has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency Check...'
                sh 'mvn dependency-check:check'  // OWASP Dependency Check: Identifies known vulnerabilities in dependencies
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Security Scan Completed',
                         body: 'The security scan has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment using Ansible...'
                sh 'ansible-playbook deploy_staging.yml'  // Ansible: Automates application deployment and configuration management
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Deployment to Staging Completed',
                         body: 'Deployment to the staging environment has completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging using Selenium...'
                sh 'pytest tests/integration'  // Selenium: A framework for automated testing of web applications
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Integration Tests on Staging Completed',
                         body: 'Integration tests on staging have completed. Check Jenkins logs for details.'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production using Kubernetes...'
                sh 'kubectl apply -f deployment.yaml'  // Kubernetes: Manages containerized applications across clusters
            }
            post {
                always {
                    mail to: "${USER_EMAIL}",
                         subject: 'Deployment to Production Completed',
                         body: 'Deployment to production has completed. Check Jenkins logs for details.'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
            mail to: "${USER_EMAIL}",
                 subject: 'Pipeline Execution Successful',
                 body: 'The entire pipeline has completed successfully.'
        }
        failure {
            echo 'Pipeline failed! Check the logs for more details.'
            mail to: "${USER_EMAIL}",
                 subject: 'Pipeline Execution Failed',
                 body: 'The pipeline has failed. Please check the Jenkins logs for more details.'
        }
    }
}
