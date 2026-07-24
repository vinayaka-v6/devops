pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'cd account-service && mvn clean install'
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                cd account-service
                sed -i 's|FROM openjdk.*|FROM eclipse-temurin:17-jdk|g' Dockerfile
                docker build -t vinayakav/repo2 .
                '''
            }
        }

        stage('Docker Push') {
            steps {
                sh '''
                docker push vinayakav/repo2
                '''
            }
        }
    }
}
