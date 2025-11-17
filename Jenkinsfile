pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Comment') {
            steps {
                script {
                    if (env.CHANGE_ID) {
                        def date = sh(returnStdout: true, script: 'date -u').trim()
                        pullRequest.comment("Build ${env.BUILD_ID} ran at ${date}")
                    } else {
                        echo 'No pull request detected; skipping comment.'
                    }
                }
            }
        }
    }
}

