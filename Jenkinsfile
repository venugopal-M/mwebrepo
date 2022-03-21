pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Code Checkout') {
            steps {
                git credentialsId: 'git_credentials', url: 'https://github.com/venugopal-M/mwebrepo.git'
                echo 'code checkout done sucessfully.'
            }
		}
            stage('Code Build') {
            steps {
            sh 'mvn clean install'
            echo 'code build done sucessfully.'
            }
            }
	    stage('Code Deploy') {
            steps {
		sshagent(['deploy_user']) {
   		sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@18.222.132.97:/opt/apache-tomcat-9.0.59/webapps"
		  }
		echo 'Stage-3 done sucessfully.'
		}
				
			}
        }
    }
