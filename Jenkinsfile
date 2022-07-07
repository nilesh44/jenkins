pipeline {

  agent any 
  
  stages{
    
      stage("pull from git"){
        steps{
       echo "stage1"
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
