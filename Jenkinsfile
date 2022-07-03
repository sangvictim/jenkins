pipeline {
    agent any
    stages {
       stage('Clone repo') {
            git branch: 'main', credentialsId: 'github-local', url: 'git@github.com:sangvictim/jenkins.git'
        }
    }
}