pipeline {

  agent any 
  environment {
   NEW_VERSION = '1.0.1-SNAPSHOT' 
  }
  
  stages{
    
      stage("pull from git"){
        steps{
       echo "stage1"
       echo env.BUILD_NUMBER
       echo env.BRANCH_NAME
       echo "version  ${env.NEW_VERSION}"  
        git branch: 'main', url: 'https://github.com/nilesh44/coffee-customer.git'
        }
   }
   
   stage("gradle build"){
     steps{
       
            bat 'gradlew.bat clean build'
           
   } 
   }
   

  }
  
  post{
   
    always{
      echo "always execute"
    }
    failure{
     echo "something has failed" 
    }
    success{
     echo "build successfull"  
    }
  }
  
}
