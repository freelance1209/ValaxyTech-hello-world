pipeline {
    agent any 
	
	tools {
  maven 'maven'
}

    {
        stages {
            
        stage("Build")
        {
            steps {
                sh script: 'mvn clean package'
            }
            
        }
        stage("stage2")
        {
            steps {
                  echo "this is first stage"
            }
        }
    }
        
   }
  }
