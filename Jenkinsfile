pipeline {
    agent any 
	tools {
			maven 'maven'
		}
	stages {
	
		stage ("Start")
		{
			steps {
					echo "Pipeline begins"
					}
			}
			
		stage ("Proceed")
		
		{
			steps 
			{
				input ("Shall we proceed with the Build")
				}
		}
		
            
        stage("Build")
			{
				steps 	{
					sh script: 'mvn package'
					}
            
			}
        stage("Deploy to Tomcat")
			{
				steps 	{
							sshagent(['Tomcat']) {
							sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Jenkins-deploy/webapp/target/*.war ec2-user@13.233.232.90:/home/ec2-user/apache/apache-tomcat-9.0.33/webapps/webapp/*.war'
    
						}
					}
			}
			
			    stage("Pipeline complete")
			{
				steps 	{
							echo "Pipeline completed"
    
						}
					
			}
    }
        
  }
