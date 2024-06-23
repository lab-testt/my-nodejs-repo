@Library('jenkins-shared-library') _

pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        GITHUB_CREDENTIALS = credentials('github') 
        DOCKER_IMAGE = 'labbtest/nodejs-postgresql'
    }

    stages {
        stage('Clone Repository') {
            steps {
                cloneRepository {
                    url 'https://github.com/lab-testt/my-nodejs-repo.git'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                buildDockerImage {
                    dockerImage DOCKER_IMAGE
                }
            }
        }

        stage('Docker Login and Push') {
            steps {
                dockerLoginAndPush {
                    credentialsId 'dockerhub'
                }
            }
        }

        stage('Install Docker Compose') {
            steps {
                installDockerCompose()
            }
        }

        stage('Deploy') {
            steps {
                deploy()
            }
        }
    }
}
