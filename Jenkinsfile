pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', credentialsId: 'github-local', url: 'https://github.com/sangvictim/jenkins'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
