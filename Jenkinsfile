node {

    stage('SCM') {
      checkout scm
    }
    
    stage('Insall Dependency'){
      sh 'composer install'
    }
    
    stage('SonarQube Analysis') {
      def scannerHome = tool 'sonarCube-scanner';
      withSonarQubeEnv() {
        sh "${scannerHome}/bin/sonar-scanner"
      }
    }

    stage('Discord Notifier'){
        discordSend title: env.JOB_NAME,
            customUsername: 'Kriwil Bot 2', 
            currentBuild.resultIsBetterOrEqualTo('SUCCESS')
    }
    
}
