node {

    stage('SCM') {
      checkout scm
    }
    
    // stage('Insall Dependency'){
    //   sh 'composer install'
    // }
    
    // stage('SonarQube Analysis') {
    //   def scannerHome = tool 'sonarCube-scanner';
    //   withSonarQubeEnv() {
    //     sh "${scannerHome}/bin/sonar-scanner"
    //   }
    // }

    stage('Discord Notifier'){
      def discordFooter = "Job: ${BUILD_TAG}"
      def discordDesc = "Branch: ${env.GIT_BRANCH}\nBuild:${BUILD_NUMBER}\nStatus:${currentBuild.currentResult}"

        discordSend description: discordDesc, 
          footer: discordFooter, 
          link: env.JOB_URL, 
          result: currentBuild.currentResult,
          title: JOB_NAME, 
          customUsername: 'Kriwil Bot', 
          webhookURL: "https://discord.com/api/webhooks/990279909484154970/XGZRI5cKJkfNIusA3RIQ5CvUTSWl0WEkC8Xit5a5GyKQ79hvxw3LEbdqBNnKMwVy_DJf"

    }
    
}
