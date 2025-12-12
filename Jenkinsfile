pipeline {
    agent any

    tools {
        jdk 'jdk11'     // Name in Jenkins Global Tools
        maven 'maven3'  // Name in Jenkins Global Tools
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
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
