pipeline {
    agent any
    stages {
        // stage("Build") {
        //     // environment {
        //     //     DB_HOST = credentials("laravel-host")
        //     //     DB_DATABASE = credentials("laravel-database")
        //     //     DB_USERNAME = credentials("laravel-user")
        //     //     DB_PASSWORD = credentials("laravel-password")
        //     // }
        //     steps {
        //         sh 'php --version'
        //         sh 'composer --version'
        //         sh 'rm composer.lock'
        //         sh 'rm -rf vendor'
        //         sh 'composer install'
        //         sh 'cp .env.example .env'
        //         // sh 'echo DB_HOST=${DB_HOST} >> .env'
        //         // sh 'echo DB_USERNAME=${DB_USERNAME} >> .env'
        //         // sh 'echo DB_DATABASE=${DB_DATABASE} >> .env'
        //         // sh 'echo DB_PASSWORD=${DB_PASSWORD} >> .env'
        //         sh 'php artisan key:generate'
        //     }
        // }

        // stage('SonarQube analysis') {
        //     // SonarQube Scanner in Global Tool Configuration
        //     environment{
        //         scannerHome = tool name: 'sonarCube-scanner';
        //     }
        //     steps{
        //     // name sonar sever in the global configure
        //     withSonarQubeEnv('sonarcube') { 
        //          sh "${scannerHome}/bin/sonar-scanner"
        //     }
        //     }
        // }

        stage('Discord Notifier'){
            environment {
                GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
                discordDesc = "Branch: ${$GIT_BRANCH}\nBuild: ${BUILD_NUMBER}\nStatus: ${currentBuild.currentResult}\n"
                discordFooter = "Build Duration: ${currentBuild.durationString}"
            }

            stage{
                discordSend description: discordDesc, 
                    footer: discordFooter,
                    link: env.JOB_URL, 
                    result: currentBuild.currentResult,
                    title: JOB_NAME, 
                    customUsername: 'Kriwil Bot', 
                    webhookURL: 'https://discord.com/api/webhooks/993056530280751144/OewXajqVs7usuWL8HRoki9KUfWVsWnmZm498Z15E0fVsFot9ZRd32ORQ1_TtK6hRgKHa'
            }


        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
