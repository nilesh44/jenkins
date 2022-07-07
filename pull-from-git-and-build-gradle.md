## jenkins should be install on your local machine and open jenkins portal on http://localhost:8080

* Note: while writing your script always remember that if your host machine operating system is linux then we should write linux command in script ,
 if it is windows then script should written using windows suitable command 

## Create new job 

![image](https://user-images.githubusercontent.com/44174633/177723933-1cbd7517-7edb-4203-97ca-52aaf5e9cc61.png)

 ## Next 
 * Enter job name , select pipeline and select ok
  
 ![image](https://user-images.githubusercontent.com/44174633/177724133-7e4f1bac-9bf6-4887-801a-3cd9f298f455.png)
 
 ## Next
 * Under pipline section , select pipeline script, add script then apply and save 
 
 ![image](https://user-images.githubusercontent.com/44174633/177724532-61bccbbf-6580-4dd8-a052-dd9f9529c2cf.png)
 
 ```
 node{
  
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
 ```
 
## Next 
* Run job by clicking on Build now

 ![image](https://user-images.githubusercontent.com/44174633/177725374-aa590805-ed0b-486f-b5c1-651133703912.png)

## Next 
* Check logs click on console logs

![image](https://user-images.githubusercontent.com/44174633/177725861-dca4b5ef-99ed-4126-9278-c4090260221f.png)

 ```
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in C:\ProgramData\Jenkins\.jenkins\workspace\first-job
[Pipeline] {
[Pipeline] stage
[Pipeline] { (pull from git)
[Pipeline] echo
stage1
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/nilesh44/coffee-customer.git
 > git.exe init C:\ProgramData\Jenkins\.jenkins\workspace\first-job # timeout=10
Fetching upstream changes from https://github.com/nilesh44/coffee-customer.git
 > git.exe --version # timeout=10
 > git --version # 'git version 2.36.0.windows.1'
 > git.exe fetch --tags --force --progress -- https://github.com/nilesh44/coffee-customer.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git.exe config remote.origin.url https://github.com/nilesh44/coffee-customer.git # timeout=10
 > git.exe config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git.exe rev-parse "refs/remotes/origin/main^{commit}" # timeout=10
Checking out Revision bd780a1f3e7d5bac56e823b57788fdf474af9983 (refs/remotes/origin/main)
 > git.exe config core.sparsecheckout # timeout=10
 > git.exe checkout -f bd780a1f3e7d5bac56e823b57788fdf474af9983 # timeout=10
 > git.exe branch -a -v --no-abbrev # timeout=10
 > git.exe checkout -b main bd780a1f3e7d5bac56e823b57788fdf474af9983 # timeout=10
Commit message: "updated name and version of api"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (gradle build)
[Pipeline] isUnix
[Pipeline] bat

C:\ProgramData\Jenkins\.jenkins\workspace\first-job>gradlew.bat clean build 
Starting a Gradle Daemon, 1 incompatible and 5 stopped Daemons could not be reused, use --status for details
> Task :clean UP-TO-DATE
> Task :compileJava
> Task :processResources
> Task :classes
> Task :bootJarMainClassName
> Task :bootJar
> Task :jar
> Task :assemble
> Task :compileTestJava
> Task :processTestResources NO-SOURCE
> Task :testClasses
> Task :test
> Task :check
> Task :build

BUILD SUCCESSFUL in 13s
8 actionable tasks: 7 executed, 1 up-to-date
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
 ```
 # We can check that build is created in our local machine 
 
 ![image](https://user-images.githubusercontent.com/44174633/177727999-dbf3cdba-31c3-4d28-a565-658f14eb44cb.png)


