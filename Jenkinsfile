
pipeline {

    agent any

    environment {
        DOCKER_IMAGE_NAME = "laweee/spring-web-app"
    }

    stages {

        stage('Build Application') {
            steps {
                echo 'Building the web application'
                sh './gradlew clean'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'build/libs/gs-serving-web-content-0.1.0.jar'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building the docker image'
            }
        }

        stage('Publish Docker Image'){
            steps {
                echo 'Publishing the docker image'
            }
        }

        stage('Deploy App to K8S Cluster') {
            steps {
                echo 'deplyoing the app to K8S'
            }
        }
    }
}