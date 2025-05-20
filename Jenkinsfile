pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Unit & Integration Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'snyk test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'ssh ec2-user@staging-server "bash deploy.sh"'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                sh 'npm run test:e2e'
            }
        }

        stage('Deploy to Production') {
            steps {
                input message: "Deploy to production?", ok: "Yes"
                sh 'ssh ec2-user@production-server "bash deploy.sh"'
            }
        }
    }
}
