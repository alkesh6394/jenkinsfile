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

        stage('push') {
            when {
                expression {
                    return env.BRANCH_NAME == 'master'
                }
            }
            steps {
                script {
                    echo "pushed"
                }
            }
        }

        stage('apply') {
            when {
                expression {
                    return env.BRANCH_NAME == 'master'
                }
            }
            steps {
                script {
                    echo "apply"
                }
            }
        }
        
        stage('No push or apply') {
            when {
                expression {
                    return env.BRANCH_NAME != 'master'
                }
            }
            steps {
                script {
                    echo "No push or apply"
                }
            }
        }
    }
}
