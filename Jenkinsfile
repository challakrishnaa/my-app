pipeline{
   agent{label 'QA-Slave'}
   tools{maven 'maven-3.8'}
  stages{
    stage('ECKOUTCODE'){
      steps{
      git 'https://github.com/challakrishnaa/my-app.git'
      }
    }
     stage('buildcode'){
        steps{
       mvn clean package 
        }
     }
  
  
  }
}
