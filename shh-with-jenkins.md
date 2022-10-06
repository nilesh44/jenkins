step 1 create global credential using cradential 
![image](https://user-images.githubusercontent.com/44174633/194362328-31a4379a-520a-47eb-8849-75c7270cf30f.png)

step 2: install sshAgent plugin
![image](https://user-images.githubusercontent.com/44174633/194362618-d0946836-d867-410a-b79f-d99b6cb02c3f.png)

step 3 : add below to execute ssh on remote location.

 sshagent(['ubuntu']) {
             //  sh 'ssh -o StrictHostKeyChecking=no -l ubuntu ec2-43-204-212-149.ap-south-1.compute.amazonaws.com uname -a 'ls''
             sh "ssh -tt ubuntu@ec2-43-204-212-149.ap-south-1.compute.amazonaws.com 'pwd;ls -a'"
               
             }
