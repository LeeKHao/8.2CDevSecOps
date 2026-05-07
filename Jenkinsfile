pipeline {
    agent any

    stages {
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
        sh '''
/opt/sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner \
  -Dsonar.login=$SONAR_TOKEN
        '''
    }
}
    }
}