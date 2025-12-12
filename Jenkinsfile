pipeline {
    agent any

    tools {
        jdk 'jdk11'     
        maven 'maven3'  
    }

    stages {

        stage('Checkout Code') {
            steps {
                
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
