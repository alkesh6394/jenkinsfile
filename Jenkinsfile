pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    git clone git@gitlab.com:clients5335643/udharibazaar/public-api.git 
                    cd public-api
                    git checkout dev
                    docker build . -t udharibazaar
                '''
            }
        }
        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }
        stage('push') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        input message: "Do you want to continue", ok: "Yes, we should"
                        echo "pushed"
                    } else {
                        echo "We cannot push"
                    }
                }
            }
        }

        stage('apply') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        input message: "Do you want to continue", ok: "Yes, we should"
                        echo "apply"
                    } else {
                        echo "We cannot apply"
                    }
                }
            }
        }
    }

    post {
        success {
            script {
                def message = "Your Jenkins Pipeline Ran Successfully"
                slackSend(channel: 'jenkins-pipeline', message: message, tokenCredentialId: 'C059M7SJL0K')
            }
        }
        failure {
            script {
                def message = "Your Jenkins Pipeline Did Not Run Successfully"
                slackSend(channel: 'jenkins-pipeline', message: message, tokenCredentialId: 'C059M7SJL0K')
            }
        }
    }
}
