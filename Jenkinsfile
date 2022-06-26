pipeline{
    agent any
    stages{
       stage('GetCode'){
            steps{
                git 'git@github.com:sangvictim/jenkins.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'composer install'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarcube') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}