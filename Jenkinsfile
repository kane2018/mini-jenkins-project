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
                sh 'php -l index.php'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mini-jenkins-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose up --build -d'
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
