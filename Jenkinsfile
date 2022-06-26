node {

    stage('SCM') {
      checkout scm
    }
    
    stage('SonarQube Analysis') {
      def scannerHome = tool 'sonarCube-scanner';
      withSonarQubeEnv() {
        sh "${scannerHome}/bin/sonar-scanner"
      }
    }
    
    stage('Insall Dependency'){
      sh 'composer install'
    }
    
    stage('Discord Notifier'){
        discordSend title: env.JOB_NAME, 
            enableArtifactsList: false, 
            webhookURL: 'https://discord.com/api/webhooks/990279909484154970/XGZRI5cKJkfNIusA3RIQ5CvUTSWl0WEkC8Xit5a5GyKQ79hvxw3LEbdqBNnKMwVy_DJf', 
            customUsername: 'Kriwil Bot 2',
            currentBuild.resultIsBetterOrEqualTo('SUCCESS'),
            result: 'SUCCESS|UNSTABLE|FAILURE|ABORTED',
    }
    
}
