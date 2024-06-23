// Jenkinsfile

@Library('your-shared-library') _

cloneRepository('github', 'https://github.com/lab-testt/my-nodejs-repo.git')

buildDockerImage('labbtest/Node.js-project:latest')

dockerLoginAndPush('labbtest/node.js-project:latest', 'dockerhub')

installDockerCompose()

deploy('docker-compose.yml')
