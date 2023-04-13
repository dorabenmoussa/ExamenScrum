pipeline {
    agent any
    environment {
        M2_HOME = "/opt/maven" // Replace this with the actual path to your Maven installation
        PATH = "${env.M2_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'ddfced83-2f1f-4c98-91b3-88979afd47b4', url: 'https://github.com/Sarrabouraui/ExamDevops.git'
            }
        }
        stage('Build') {
            steps {
                //sh 'export M2_HOME = "/opt/maven"'
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
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
    }
}
