pipeline{
    agent any    

            stages {
            
                stage("Clean Workspace and clone initial repo") {
                            steps{
                                withCredentials([usernamePassword(credentialsId: 'github-user', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                                    cleanWs()
                                    sh "git clone https://${USERNAME}:${PASSWORD}@github.com/juanmatomas07/jenkins.git"
                                    }
                                    
                                }
                     }
                   
                stage("Build-app") {
                    steps {         
                        withCredentials([usernamePassword(credentialsId: 'github-user', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                           sh '''docker build -t tomcast . \
                           && docker run -p 8081:8080 tomcast_cluster'''                                     
                            }
                      }
                }
            }
         }
