@Library("shared") _
pipeline {
    agent any
    
    stages {
        stage('code') {
            steps {
                script{
                    clone("main", "git-hub", "https://github.com/WiseAdnan/django-notes-app.git")
                } 
            }
        }
        
        stage('build') {
            steps {
                script{
                Build("notes-app", "latest", "shahabadnan")
                }
            }
        }    

        stage('push to DockerHub') {
            steps {
                script{
                    DockerPush("notes-app", "latest")
                }
            }
        }

        stage('deploy') {
            steps {  
                echo 'this is a deploy step'
                sh 'docker-compose up -d'
            }    
        }
        
        
    }
}
    
