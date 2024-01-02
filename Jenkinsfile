pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    def mvnHome = tool 'Maven_Home'
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def mvnHome = tool 'Maven_Home'
                    sh 'mvn test'
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts 'target/*.jar'
        }
    }
}
