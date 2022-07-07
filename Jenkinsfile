pipeline {

  agent any 
  
  stages{
    
      stage("pull from git"){
       echo "stage1"
        git branch: 'main', url: 'https://github.com/nilesh44/coffee-customer.git'
   }
   
   stage("gradle build"){
       if(isUnix()){
           sh './gradlew clean build'

       }
       else{
            bat 'gradlew.bat clean build'
           }
   } 
  
   

  }
  
}
