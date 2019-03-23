
pipeline {

    agent any

    stages {

        stage('Build Application') {
            steps {
                echo 'Building the application'
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