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
              env GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
                echo "branch: ${env.GIT_BRANCH} -$BRANCH_NAME"
            }
        }
        stage ('Build Skipped') {
            steps {
                echo 'Skipped full build.'
            }
        }
    }
}
