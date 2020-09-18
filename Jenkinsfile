node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/shivaramkhanal/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  
  stage('Deploy to Tomcat'){
	  sshagent(['demo-tomcat']) {
	    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@:3.87.62.161/opt/tomcat9/webapps/'
	}
  
	}
  
}
