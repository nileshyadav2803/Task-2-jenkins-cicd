pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t task-2-jenkins-cicd .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker image inspect task-2-jenkins-cicd'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker run -d --name task2-app -p 8080:80 task-2-jenkins-cicd'
            }
        }
    }
}