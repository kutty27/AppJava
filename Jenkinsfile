pipeline {
    agent any
    
    tools
    {
    maven 'Maven_Home'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    bat "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    bat "mvn -Dmaven.test.failure.ignore=true test"
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
