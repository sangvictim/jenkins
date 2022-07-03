pipeline {
    agent any
    stages {
        stage("Build") {
            // environment {
            //     DB_HOST = credentials("laravel-host")
            //     DB_DATABASE = credentials("laravel-database")
            //     DB_USERNAME = credentials("laravel-user")
            //     DB_PASSWORD = credentials("laravel-password")
            // }
            steps {
                sh 'php --version'
                sh 'composer --version'
                sh 'rm composer.lock'
                sh 'rm -rf vendor'
                sh 'composer install'
                sh 'cp .env.example .env'
                // sh 'echo DB_HOST=${DB_HOST} >> .env'
                // sh 'echo DB_USERNAME=${DB_USERNAME} >> .env'
                // sh 'echo DB_DATABASE=${DB_DATABASE} >> .env'
                // sh 'echo DB_PASSWORD=${DB_PASSWORD} >> .env'
                sh 'php artisan key:generate'
            }
        }

        stage('SonarQube Analysis') {
            steps{
                withSonarQubeEnv('sonarCube-scanner') {
                    tool name: 'sonarCube-scanner'
                }
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
