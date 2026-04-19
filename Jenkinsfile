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
                sh 'sudo cp -r * /var/www/html/'
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}
