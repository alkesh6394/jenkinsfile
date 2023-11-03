pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
               sh ''' git clone git@gitlab.com:clients5335643/udharibazaar/public-api.git 
                cd public-api
                docker build . -t udharibazaar
                '''
                
            }
        }
        
        
         stage('push'){
            input{
                message "Do you want to continue"
                ok "Yes we should"
            }
            steps{
             script{
                   if (env.BRANCH_NAME=='master'){
                  echo "pushed"
        }
                  else{
            echo "we cannot pushed"
        }
             }
            }
        }
        
        
         stage('apply'){
            input{
                message "Do you want to continue"
                ok "Yes we should"
            }
            steps{
             script{
                   if (env.BRANCH_NAME=='master'){
                     echo "apply"
                  }
                  else{
            echo "we cannot apply"
        }
             }
            }
        }
    }
}
