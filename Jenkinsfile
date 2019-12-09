pipeline{
    agent any    

            stages {
            
                stage("Clean Workspace and clone initial repo") {
                            steps{
                                withCredentials([usernamePassword(credentialsId: 'github-user', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                                    cleanWs()
                                   sh '''git clone https://${USERNAME}:${PASSWORD}@github.com/juanmatomas07/test.git \
                            && docker build -t app . \
                            && docker run -p 8081:8080 app'''
                                    }
                                    
                                }
                     }
                   
                
            }
         }
