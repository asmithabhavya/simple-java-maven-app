pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {
        stage('Git Repo & Clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Install') {
            steps {
                bat 'mvn install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }
    post {
    success {
        emailext(
            subject: "SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
            body: "Your Jenkins build was successful!",
            to: "your-email@gmail.com"
        )
    }

    failure {
        emailext(
            subject: "FAILED: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
            body: "Your Jenkins build failed. Check the console output.",
            to: "asmithabhavya@gmail.com"
        )
    }
}
}
