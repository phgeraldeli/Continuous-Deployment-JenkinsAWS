pipeline {
    
    agent any
    tools {
        jdk 'jdk_1.8.0'
        maven 'Maven'
    }

    stages {
        stage('Compilando') {
            steps {
                sh 'mvn clean install -DskipTests' 
            }
        }

        stage('Testando') {
            steps {
                sh 'mvn verify'
            }
        }

    }
}