pipeline {

  agent any 
  
  //declearing user defined environment veriable
  properties([
      parameters([
        string(description: 'git repo url', name: 'url', trim: true), 
        choice(choices: ['dev,prod,QA'], description: 'environment', name: 'select env'),
        string(description: 'branch of git repo', name: 'branch', trim: true)
      ])
    ])
               
  environment {
   NEW_VERSION = '1.0.1-SNAPSHOT' 
  }
  
  stages{
    
      stage("pull from git"){
        steps{
       echo "stage1"
          
                echo "url ${params.url}"
                echo "branch: ${params.branch }"

                echo "environment: ${params.environment}"

          
       // this environment veriable is provide by jenkins
          //we can check at http://localhost:8080/env-vars.html/
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
  
  //this will execute after completion of all stages
  post{
   
    //this block will always execute
    always{
      echo "always execute"
    }
    //this block will execute on failure
    failure{
     echo "something has failed" 
    }
    
    //this block will execute on success
    success{
     echo "build successfull"  
    }
  }
  
}
