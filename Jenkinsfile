pipeline {
    agent any

    stages {
stage('Test Credential') {
    steps {
        withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
            sh 'echo TOKEN_FOUND'
        }
    }
}
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/LeeKHao/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                sh 'npm audit || true'
            }
        }
	stage('SonarCloud Analysis') {
    steps {
        withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
            sh '''
            cd /var/jenkins_home/workspace/8.2CDevSecOps

            /opt/sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner \
            -Dsonar.token=$SONAR_TOKEN
            '''
        }
    }
}
	}
}