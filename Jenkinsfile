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
	    sh 'scp -i StrictHostKeyChecking=no target/*.war ubuntu@3.95.168.106:/opt/tomcat9/webapps/'
            //sh 'scp -i /home/ec2-user/jenkins-demo.pem -o StrictHostKeyChecking=no target/*.war ec2-user@100.26.175.204:/opt/tomcat9/webapps/'  
	
   // sh 'scp -i /code.pem -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/JenkinsPipeline/target/*.war ubuntu@:3.95.168.106/opt/tomcat8/webapps/'
		 //  sh "scp -v -o StrictHostKeyChecking=no -i /var/lib/jenkins/.ssh/code.pem **/target/*.war ubuntu@:3.95.168.106:/var/lib/tomcat/webapps"
	}
  
	}
  
}
