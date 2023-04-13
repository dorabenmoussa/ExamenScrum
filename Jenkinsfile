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
        stage('SonarQube Analysis') {
            steps {
                
                sh "mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=root"

            }
        }
        stage('Nexus Publish') {
            steps {
                nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: 'target/*.jar']], mavenCoords: [artifactId: 'my-app', groupId: 'com.example', version: '1.0']]]
            }
        }
        stage('Display Date') {
            steps {
                sh 'date'
            }
        }
    }
}
