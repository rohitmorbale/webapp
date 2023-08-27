pipeline {
    agent any
    tools {
        maven 'Maven' // Make sure the tool name matches the configured name
    }
    stages {
        stage('Initialize') {
            steps {
                sh '''
                 echo "PATH = ${PATH}"
                 echo "M2_HOME = ${M2_HOME}"
                 '''
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package' // Example Maven command
            }
        }
    }
}



