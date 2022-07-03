node {
  stage('Checkout SCM') {
    checkout scm

  }

    // stage('Insall Dependency'){
    //   sh 'rm composer.lock'
    //   sh 'composer install'
    // } 

    // stage('SonarQube Analysis') {
    //   def scannerHome = tool 'sonarCube-scanner';
    //   withSonarQubeEnv() {
    //     sh "${scannerHome}/bin/sonar-scanner"
    //   }
    // }

    stage('Discord Notifier'){
      def GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
      def discordDesc = "Branch: ${$GIT_BRANCH}\nBuild: ${BUILD_NUMBER}\nStatus: ${currentBuild.currentResult}\n"
      def discordFooter = "Build Duration: ${currentBuild.durationString}"

        discordSend description: discordDesc, 
          footer: discordFooter,
          link: env.JOB_URL, 
          result: currentBuild.currentResult,
          title: JOB_NAME, 
          customUsername: 'Kriwil Bot', 
          webhookURL: 'https://discord.com/api/webhooks/993056530280751144/OewXajqVs7usuWL8HRoki9KUfWVsWnmZm498Z15E0fVsFot9ZRd32ORQ1_TtK6hRgKHa'

    }
}
