
pipeline {
    agent any
	stages {
	stage('Code Checkout') {
            steps {
			git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
			echo "Code Checkout executed."
			      }
			}
	stage('Code Build') {
            steps {
			sh 'mvn clean install'
			echo "Code Build executed."
			      }
			}
	stage('Code Deploy') {
            steps {
			sshagent(['deploy_user']) {
    sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@13.233.74.200:/opt/apache-tomcat-8.5.35/webapps"
              }
			
			      }
			}
	}

}
