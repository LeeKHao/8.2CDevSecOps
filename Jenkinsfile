pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building application using npm'
                sh 'npm install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests'
                sh 'npm test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running SonarQube analysis'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running OWASP Dependency-Check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running staging tests'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server'
            }
        }
    }
}