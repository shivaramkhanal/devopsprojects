node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/shivaramkhanal/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  
  stage('Deploy to Tomcat'){
	  
	  sshagent(['shivaram']) {
          sh 'who'
	  sh 'scp -i /var/lib/jenkins/code.pem -o StrictHostKeyChecking=no target/*.war ubuntu@100.26.175.204:/opt/tomcat9/webapps/'
	
	}
  
	}
  
}
