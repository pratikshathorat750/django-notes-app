@Library("Shared") _
pipeline{
    agent{ label "vinod" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               echo "This is cloning the code" 
               git url: "https://github.com/LondheShubham153/django-notes-app.git" , branch:"main"
               echo "Code Cloning successful" 
            }
        }
         stage("Build"){
            steps{
               script{
                  docker_build("notes-app","latest","pratikshathorat750")
          }
        }
     }
        stage("Push to DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","pratikshathorat750")
               }
          }
       }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
                
            }
        }
    }
}
