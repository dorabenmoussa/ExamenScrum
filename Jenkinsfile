pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/dorabenmoussa/ExamenScrum.git'
            }
        }
        stage('Display Date') {
            steps {
                sh 'date'
            }
        }
    }
}
