pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kane2018/mini-jenkins-project.git'
            }
        }

        stage('Test') {
            steps {
                bat 'php -l index.php'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t mini-jenkins-app .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker-compose down || true'
                bat 'docker-compose up --build -d'
            }
        }
    }

    post {
        success {
            echo "✅ Déploiement réussi !"
        }
        failure {
            echo "❌ Le pipeline a échoué"
        }
    }
}
