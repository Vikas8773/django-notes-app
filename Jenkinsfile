@Library("Shared") _
pipeline{
    agent { label "vinod" }
    
    stages{
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/Vikas8773/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    dockerbuild("django-notes-app", "latest", "vikassangale")
                }
            }
        }
        stage("Test"){
            steps{
                echo "This is Testing a code"
            }
        }
        stage("Push to DockerHub"){
            steps{
                echo "Pushing image..."
                script {
                    docker_push("django-notes-app", "latest")
                }
            }
        }
        stage("Deploy"){
            
            steps {
                echo "This is deploying a code"
                script{
                    docker_compose()
                }
            }
        }
    }
}
