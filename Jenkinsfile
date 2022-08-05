pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage('Release') {
          steps {
               sh '''
                    oc project avissg-greetings
                    oc start-build greeting-console --follow --wait
               '''
          }
        }
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        // Add the Release stage here
    }
}
