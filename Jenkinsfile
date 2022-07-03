pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
