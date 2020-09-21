node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  
  stage('Deploy to Tomcat'){
	  sshagent(['shivaram']) {
	    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@54.211.232.145:/opt/tomcat9/webapps/'
	}
  
	}
	
stage('Slack Notification'){
	
         slackSend  baseUrl: 'https://hooks.slack.com/services/',channel: 'jenkins-demo', color: '#439FE0', message: 'Build Started:${env.JOB_NAME} ${BUILD_NUMBER}', tokenCredentialId: 'jenkins-dem'
         }
}
