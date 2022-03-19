pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Code Checkout') {
            steps {
                git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
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
   		sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@3.93.3.196:/opt/apache-tomcat-9.0.60/webapps"
		  }
		echo 'Stage-3 done sucessfully.'
		}
				
			}
        }
    }
