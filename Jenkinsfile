pipeline {
    agent any

    stages {
        stage('Security Scan') {
            steps {
                sh 'trivy image --exit-code 1 --severity CRITICAL,HIGH zhumagalikarakat/java-app:v2'
            }
        }
    }
}
