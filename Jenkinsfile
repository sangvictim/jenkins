pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh 'php --version'
                sh 'rm composer.lock'
                sh 'rm vendor'
                sh 'composer install'
                sh 'composer --version'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
