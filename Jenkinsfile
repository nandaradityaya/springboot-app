pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/nandaradityaya/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t nandaradityaya/springboot-app:v3 .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push nandaradityaya/springboot-app:v3
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}