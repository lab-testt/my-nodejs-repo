@Library('jenkins-shared-library') _

pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'dockerhub'
        GITHUB_CREDENTIALS = credentials('github')
        DOCKER_IMAGE = 'labbtest/nodejs-postgres-app'
    }

    stages {
        cloneRepository {
            branch = 'main'
            credentialsId = 'github'
            url = 'https://github.com/lab-testt/my-nodejs-repo.git'
        }

        buildDockerImage()

        dockerLogin()

        installDockerCompose()

        deploy()
    }
}
