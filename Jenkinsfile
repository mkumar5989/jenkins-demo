pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/mkumar5989/jenkins-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop jenkins-app || true
                docker rm jenkins-app || true
                docker run -d -p 8081:80 --name jenkins-app jenkins-demo-app
                '''
            }
        }
    }
}
