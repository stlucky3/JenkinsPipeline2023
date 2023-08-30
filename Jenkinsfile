pipeline {
    agent any
	stages {
	   stage (' Checkout From GitHub Repository') {
		steps { 
		    checkout scm
		}
	   }
           stage (' Maven Tool Build and Test Code') {
		steps {
		     script {
			  sh 'mvn clean install'
		     }
		}
	   }
	  stage('SonarQube Code Analysis') {
            steps {
                script {
                    withSonarQubeEnv('SonarQube') {
                        sh 'mvn sonar:sonar -Dsonar.host.url=$SONAR_URL'
                           
                    }
                }
            }
        }	
    }
}	
	    
