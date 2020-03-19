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
					sh script: 'mvn clean package'
					}
            
			}
        stage("Deploy to Tomcat")
			{
				steps 	{
							sshagent(['Tomcat']) {
							sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Jenkins-pipeline/webapp/target/*.war ec2-user@172.31.32.222:/home/ec2-user/tomcat/apache-tomcat-9.0.31/webapps'
    
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
        
  }
