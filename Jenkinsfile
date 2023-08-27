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
	    stage ('Check-Git-Secrets') {
	    steps {
		sh 'rm trufflehog || true'  
		sh 'docker run gesellix/trufflehog --json https://github.com/rohitmorbale/webapp.git > trufflehog'  
		sh 'cat trufflehog'    
	    }
		    
	    }
	    
	   
        stage('Build') {
            steps {
                sh 'mvn clean package' // Example Maven command
            }
        }
        stage('Deploy-To-Tomcat') {
           steps {
             sshagent(['tomcat']) {
                      sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.127.191.18:/home/ubuntu//prod/apache-tomcat-10.1.13/webapps/webapp.war'

                }
            }
		}	
    }
}




