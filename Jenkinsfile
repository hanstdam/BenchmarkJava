pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}