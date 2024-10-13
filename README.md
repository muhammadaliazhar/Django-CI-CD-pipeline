# Django-CI-CD-pipeline
This a a CI/CD pipeline file for Django app

pipeline {
    agent { label "agent1" }
    
    stages {
        stage('Code') {
            steps {
                echo 'This is cloning the code from GitHub'
                git url: "https://github.com/muhammadaliazhar/django-notes-app.git", branch:"main"
		        echo 'code clone successfully'
            }
        }
        stage('Build') {
            steps {
                echo 'This is building code from Docker'
		        sh "whoami"
		        sh "docker build -t notes-app:latest ."
		        echo 'code build from docker successfully'
            }
        }
        stage('Test') {
            steps {
                echo 'This is testing the code'
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is deploying the code'
                sh "docker compose up -d"
            }
        }
    }
}
