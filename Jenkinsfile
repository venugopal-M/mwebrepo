pipeline {
    agent any
   environment {
        PATH = "/opt/maven/bin:$PATH"
    }
stages {
        stage('CodeCheckout') {
            steps {
		  git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
		  echo 'Code Checkout done sucessfully.'
		  }
				}
        stage('Code build ') {
            steps {
		  sh 'mvn clean install'
                  echo 'Code build done sucessfully.'
		  }
				}
        stage('CodeDeploy') {
            steps {
	sshagent(['deploy_user']) {
  		     sh "scp  -o StrictHostKeyChecking=no  webapp/target/webapp.war  ec2-user@54.221.143.96:/opt/apache-tomcat-8.5.35/webapps"
			}
		  echo "Code deploy done sucessfully."
		  }
				}
     

}
}
