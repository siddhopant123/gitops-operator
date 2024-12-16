pipeline {
    agent any

   

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            environment {
                SONAR_HOST_URL = 'http://192.168.27.55:9000'
                SONAR_AUTH_TOKEN = credentials('sonarqube-user-token') // Jenkins credentials ID
            }
            steps {
                sh '''
                /var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarScanner/bin/sonar-scanner \
                    -Dsonar.projectKey=siddhopant123_gitops-operator_45779f24-0b18-447f-9076-8d5e437d9d4c \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=$SONAR_HOST_URL \
                    -Dsonar.token=$SONAR_AUTH_TOKEN \
                    -Dsonar.projectBaseDir=/var/lib/jenkins/workspace/gitops-application
                '''
            }
        }
    }
}
