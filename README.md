# Website-Development-with-Jenkins-job-on-AWS-EC2

PROJECT-II

*Website Development with Jenkins job on AWS-EC2*

A Continous Integration & Continous Deployment demonstrating the Jenkins Job and how it is works for a website development project.

Technologies Used - Jenkins, AWS-EC2, Ubuntu, Apache2, Git & Github


-------------------------------------------------------------------------------------------------------------------------------------------------------------


Step :-

1.Launch the EC2 Instance in AWS-Ubuntu

2.Install the Jenkins in EC2-Instance and Access the Jenkins

3.Configure the Job and write the required command in execution shell

4.Build the Jenkins Job

5.It will Install the Webserver in EC2-Instance and Jenkins connected with Github repository as well as Webserver

6.In every commit jenkins will pull the code from github and deploy into the webserver


-------------------------------------------------------------------------------------------------------------------------------------------------------------

All Steps in details with Commands:-


-----------------------------------AWS EC2 Instance-----------------------------------


- Click on EC2 service 

- Click on the Launch Instance

- Choose AMI

      Ubuntu
      
- Choose an Instance Type
      
      t2.micro
      
- Configure Instance Details

      Number of Instance = 1
      Network = Default
      Subnet = Default
      Auto-Assign Public IP = Use subnet setting (Enable)
      
- Add Storage

      Root - /dev/xvda  - Size-8GB  -- Default
      
- Add Tags 

      Name - Ubuntu
      
- Configure the Security Group

      Select - Create a new security group 
      Security group name = sg-jenkins
      
      
      -Type-----Protocol-----Port-----Source-
      
      SSH ---------------TCP---------22-------Anywhere
      HTTP---------------TCP---------80-------Anywhere
      HTTPS--------------TCP---------443------Anywhere
      Custom TCP Rule----TCP---------8080-----Anywhere
      
      
- Click on Review and Launch

- Access the amazonlinux2 via the putty 
