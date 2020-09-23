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
	   sh 'who'
	  sh 'scp -i /var/lib/jenkins/code.pem -o StrictHostKeyChecking=no target/*.war ubuntu@34.238.155.111:/opt/tomcat9/webapps/'
	}
  
	}
	
stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkinsnotification', color: '#fc0324', message: 'New Build deployed by prabhat', teamDomain: 'intelycoreworkspace', tokenCredentialId: 'slack-secret'
	}
	
stage('Email Notification'){
	//mail bcc: '', body: 'build success done', cc: '', from: 'prabhat@aptence.com', replyTo: 'prabhatiitbhu@gmail.com', subject: 'build success by prabhat', to: 'prabhatiitbhu@gmail.com'
	emailext body: 'success done !!', subject: 'jenkins work email', to: 'shiva.khanal20@gmail.com'
}
	
  
}
