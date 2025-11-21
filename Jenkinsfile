@Library("Shared") _
pipeline {
    agent any

    stages {

        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                script {
                    clone("https://github.com/harshalp1275/django-notes-app.git", "feature-harsh-test-django-app")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    build("note-app", "latest", "harshalpatil1010")
                }
            }
        }

        stage("Push to Docker Hub") {
            steps {
                script {
                    docker_push("note-app", "latest", "harshalpatil1010")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying the Docker Compose services..."
                sh "docker compose down && docker compose up -d"
            }
        }

    } // end stages
}   // end pipeline
