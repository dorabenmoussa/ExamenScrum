pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Récupération du code depuis Github
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/dorabenmoussa/ExamenScrum.git']]])
            }
        }
        stage('Build') {
            steps {
                // Compilation avec Maven
                sh 'mvn clean compile'
            }
        }
        // ... Autres étapes du pipeline
    }
}
