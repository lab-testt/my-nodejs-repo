@Library('jenkins-shared-library@main') _

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
                script {
                    echo 'Starting Clone Repository stage...'
                    cloneRepository {
                        url 'https://github.com/lab-testt/my-nodejs-repo.git'
                    }
                                echo 'Clone Repository stage completed.'

                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Starting Build Docker Image stage...'
                    buildDockerImage {
                        dockerImage DOCKER_IMAGE
                    }
                }
            }
        }

        stage('Docker Login and Push') {
            steps {
                script {
                    echo 'Starting Docker Login and Push stage...'
                    dockerLoginAndPush {
                        credentialsId 'dockerhub'
                    }
                }
            }
        }

        stage('Install Docker Compose') {
            steps {
                script {
                    echo 'Starting Install Docker Compose stage...'
                    installDockerCompose()
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Starting Deploy stage...'
                    deploy()
                }
            }
        }
    }
}
