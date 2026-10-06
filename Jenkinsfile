pipeline {
    agent any

    stages {
        stage('Security Scan') {
            steps {
                sh 'trivy image --exit-code 1 --severity CRITICAL,HIGH zhumagalikarakat/java-app:v2'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
