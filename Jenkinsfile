pipeline {
    agent any
    environment {
        M2_HOME = "/opt/maven" // Replace this with the actual path to your Maven installation
        PATH = "${env.M2_HOME}/bin:${env.PATH}"
    }
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
