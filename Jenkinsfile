@Library("shared-library") _
pipeline {
    agent any

    stages {
        stage('clone repo') {
            steps {
                //sh 'sudo apt install -y speedtest-cli'
                //git branch: 'main', url: 'https://github.com/coooolk/django-notes-app.git'
                //echo 'cloning successfull'
                script{
                    clone("https://github.com/coooolk/django-notes-app.git", "main")
                }
                
            }
        }
        //stage('stopping all containers') {
         //   steps{
         //       sh 'docker compose down'
         //   }
        //}
        stage('building image') {
            steps {
                //sh 'docker build -t django-notes-app:latest .'
                //sh 'whoami'
                //echo 'building image successful'
                script{
                    docker_build("coooolkpk", "django-notes-app", "latest")
                }
            }
        }
        stage('pushing image') {
            steps{
                script{
                    docker_push("coooolkpk", "django-notes-app", "latest")
                }
            }
        }
        stage('deploying image') {
            steps {
                sh 'docker compose down && docker compose up -d'
            }
        }
    }
}
