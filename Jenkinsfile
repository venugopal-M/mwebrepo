pipeline {
    agent any
   environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
       stage('CodeCheckOut') {
           
                       steps {
               
			 git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
               
				echo 'CodeCheckout done successfully'
           
			   }
				}
            stage('CodeBuild') {
            steps {
		sh 'mvn clean install'
            	echo 'Code build done sucessfully.'
            }
            }
	    stage('Stage-3') {
            steps {

		sshagent(['deploy_user']) {

   		sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@3.83.133.180:/opt/apache-tomcat-8.5.35/webapps"
		echo 'Code deployment done sucessfully.'
		  }
		
		  }
				
			}
        }
    }
