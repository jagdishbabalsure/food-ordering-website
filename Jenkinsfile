pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/jagdishbabalsure/food-ordering-website.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Build Started'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Testing Application'
            }
        }

        stage('Deploy') {
        steps {
            sh '''
            cp index.html /var/www/html/
            cp style.css /var/www/html/
            cp script.js /var/www/html/
            cp -r images /var/www/html/
            sudo systemctl restart nginx
            '''
        }
    }
    }
}
