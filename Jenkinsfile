pipeline {

  agent any 
  
  //declearing user defined environment veriable
 parameters {
    choice(
      name: 'Env',
      choices: ['DEV', 'QA', 'UAT', 'PROD'],
      description: 'Passing the Environment'
    )
       string(
         name: 'URL', 
         defaultValue: '', 
         description: 'url of git repo',
         trim: true)

        string(
          name: 'BRANCH', 
          defaultValue: '', 
          description: 'branch',
          trim: true)
   
   string(
          name: 'sonarProjectkey', 
          defaultValue: '', 
          description: 'sonar-project-key',
          trim: true)
   
   string(
          name: 'sonarUrl', 
          defaultValue: 'http://localhost:9000', 
          description: 'sonar-url',
          trim: true)
        
  
  string(
          name: 'sonarUsername', 
          defaultValue: 'admin', 
          description: 'sonar-username',
          trim: true)
        
  
string(
          name: 'sonarPassword', 
          defaultValue: 'admin4', 
          description: 'sonar password',
          trim: true)
        
  }
               
  environment {
   NEW_VERSION = '1.0.1-SNAPSHOT' 
  }
  
  stages{
    
      stage("pull from git"){
        steps{
       echo "stage1"
          
                echo "Env ${params.Env}"
               echo "Env ${params.URL}"
               echo "Env ${params.BRANCH}"
          
       // this environment veriable is provide by jenkins
          //we can check at http://localhost:8080/env-vars.html/
       echo env.BUILD_NUMBER
       echo env.BRANCH_NAME
          
       echo "version  ${env.NEW_VERSION}"  
        git branch: "${params.BRANCH}" , url:  "${params.URL}"
        }
   }
   
   stage("gradle build"){
     steps{
       
            bat 'gradlew.bat clean build'
           
   } 
   }
    stage("sonarqube"){
     steps{
       
            bat "gradlew.bat sonarqube -Dsonar.projectKey=${params.sonarProjectkey} -Dsonar.host.url=${params.sonarUrl} -Dsonar.login=${params.sonarUsername} -Dsonar.password=${params.sonarPassword}"
           
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
