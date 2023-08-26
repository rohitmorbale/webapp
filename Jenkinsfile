pipeline {
    agent any
    tools {
        maven 'Maven' // Make sure the tool name matches the configured name
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install' // Example Maven command
            }
        }
    }
}

