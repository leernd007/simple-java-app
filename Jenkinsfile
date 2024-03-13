pipeline {
    agent any
    tools {
        maven "maven 3"
        jfrog 'jfrog-cli'
    }
    environment {
        ARTIFACTORY_REPO = 'andrii-java-app-generic-local'
        ARTIFACTORY_URL = 'https://gddfg.jfrog.io/artifactory'
        CREDENTIALS_ID = 'jfrog-cli-access-token'
        GIT_REPO = 'https://github.com/leernd007/simple-java-app'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: "${GIT_REPO}"
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean install -DskipTests'
            }
        }
        stage('Deploy to Artifactory') {
            steps {
                script {
                    def rtServer = Artifactory.newServer url: "${ARTIFACTORY_URL}", credentialsId: "${CREDENTIALS_ID}"
                    def buildInfo = Artifactory.newBuildInfo()
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "target/*.jar",
                                "target": "${ARTIFACTORY_REPO}/"
                            }
                        ]
                    }"""
                    def buildInfoResponse = rtServer.upload(uploadSpec)
                    echo "${buildInfoResponse}"
                }
            }
        }
    }
}