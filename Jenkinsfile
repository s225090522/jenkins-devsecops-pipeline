pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo ' Mvn used for buildin'
            }
        }

        stage('Unit & Integration Tests') {
            steps {
                echo 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'snyk test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'ssh ec2-user@staging-server "bash deploy.sh"'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'npm run test:e2e'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'ssh ec2-user@production-server "bash deploy.sh"'
            }
        }
    }
}
