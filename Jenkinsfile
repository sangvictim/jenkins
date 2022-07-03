pipeline {
  agent any
    stages {
        stage ('Prepare') {
            steps {
                checkout scm
            }
        }

        stage ('Build') {
            steps {
              GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
                echo "branch: ${GIT_BRANCH}"
            }
        }
        stage ('Build Skipped') {
            steps {
                echo 'Skipped full build.'
            }
        }
    }
}
