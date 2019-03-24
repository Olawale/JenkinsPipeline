
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
            when {
                branch 'master'
            }
            steps {
                script {
                    app = docker.build(DOCKER_IMAGE_NAME)
                    app.inside {
                        sh 'echo Hello World'
                    }
                }
            }
        }

        stage('Publish Docker Image'){
            steps {
                script {
                    docker.withRegistry('', 'docker_hub') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }

        stage('Delete Docker Image'){
            steps {
                sh "docker rmi $DOCKER_IMAGE_NAME:$BUILD_NUMBER"
                sh "docker rmi $DOCKER_IMAGE_NAME:latest"
            }
        }

        stage('Deploy App to K8S Cluster') {
            steps {
                input 'Are you sure you want to deploy to Production?'
                milestone(1)
                echo 'Deploying to K8S'
            }
        }
    }
}