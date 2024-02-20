pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvnw clean install'
            }
        }
        stage('Docker') {
            steps {
                script {
                    bat 'docker stop app || exit 0' 
                    bat 'docker rm app || exit 0' 
                    bat 'docker build -t myapp .'
                    bat 'docker run -d --name app -p 8888:8080 myapp'
                }
            }
        }
    }
}
