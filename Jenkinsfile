pipeline{
	agent any
	tools{
	maven 'maven3.8'
	}
	stages{
		stage('checkoutcode'){
			steps{
			git branch: 'master', url: 'https://github.com/challakrishnaa/my-app.git'
			}
		}
		stage('buildingcode'){
			steps{
			sh 'mvn clean package'
			}
		}
		stage('deploy'){
			steps{
			sshagent(['tomcat8_multi']) {	
                      sh 'scp -o StrictHostKeyChecking=no target/myweb-1.0.war ec2-user@3.88.194.243:/opt/tomcat8/webapps'
              }
			}
		}
		
		
	}
}
