@Library("Shared") _
pipeline{
    agent{label "vinod"}
    stages{
         stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                 script{
                clone("https://github.com/durgaprasad2882/django-notes-app.git", "main")
                    }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","dgprasad82")
                }
            }
        }        
        stage("Test"){
            steps{
                echo "This is Testing the code"
            }
        }
         stage("Push to DockerHub"){
            steps{
               
               script{
                    docker_push("notes-app","latest","dgprasad82")
               }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
                
            }
        }
    }
}
