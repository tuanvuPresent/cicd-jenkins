pipeline {
    agent any
    options {
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
			when {
                expression {
                    GIT_BRANCH = 'origin/' + sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
                    return env.GIT_BRANCH == 'origin/develop'
                }
            }
            steps {
                echo 'Start build'
                echo 'End build'
            }
        }
    }
    post {
        always {
            dir("${env.WORKSPACE}cicd-jenkins@tmp") {
                deleteDir()
            }
        }
    }
}
