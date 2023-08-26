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
            post{
                success
                {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
           steps {
               deploy adapters: [tomcat9(path: '', url: 'http://13.127.191.18:8080/')], contextPath: null, war: '**/*.war'
            }
        }

    }
}



