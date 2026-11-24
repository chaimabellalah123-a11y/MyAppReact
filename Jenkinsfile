pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/chaimabellalah123-a11y/MyAppReact.git'
            }
        }

        stage('Build Server Image') {
            steps {
                bat 'docker build -t mern-server ./Server'
            }
        }

        stage('Build Client Image') {
            steps {
                bat 'docker build -t mern-client ./Client'
            }
        }

        stage('Stop Old Containers') {
            steps {
                bat 'docker compose down'
            }
        }

        stage('Run with Docker Compose') {
            steps {
                bat 'docker compose up -d --build'
            }
        }

        stage('Verify') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès : application MERN déployée.'
        }
        failure {
            echo 'Le pipeline a échoué, consultez les logs.'
        }
    }
}