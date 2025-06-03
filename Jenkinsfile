pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    stages {
        stage('Verify Java') {
            steps {
                sh 'java -version'
            }
        }
        stage('Verify Maven') {
            steps {
                sh 'mvn -version'
            }
        }
    }
}