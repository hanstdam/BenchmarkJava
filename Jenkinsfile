pipeline {
    agent any
    stages {
        stage('Install Maven') {
            steps {
                sh 'curl -sL https://downloads.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz | tar xz && mv apache-maven-* /opt/maven && ln -s /opt/maven/bin/mvn /usr/local/bin/mvn'
            }
        }
        stage('Verify Maven') {
            steps {
                sh 'mvn -version'
            }
        }
    }
}