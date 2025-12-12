pipeline {
    agent any

    tools {
        jdk 'jdk11'     // Name in Jenkins Global Tools
        maven 'maven3'  // Name in Jenkins Global Tools
    }

    stages {

        stage('Checkout Code') {
            steps {
                // Correct way to use credentialsId
                git branch: 'main',
                    url: 'https://github.com/AbdallahSWDev/jenkins.git',
                    credentialsId: 'github-cred'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
