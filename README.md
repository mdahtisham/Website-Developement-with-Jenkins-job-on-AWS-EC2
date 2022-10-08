# Website-Development-with-Jenkins-job-on-AWS-EC2

PROJECT-II

*Website Development with Jenkins job on AWS-EC2*

A Continous Integration & Continous Deployment demonstrating the Jenkins Job and how it is works for a website development project.

Technologies Used - Jenkins, AWS-EC2, Apache2, Git & Github


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

- Access the EC2-Instance-Ubuntu via the putty 



-----------------------------------AmazonLinux-----------------------------------

- Command for root access

      $ sudo su
      
- Update

      [root@ip--] # apt-get update -y
      
- Install the Jdk

      [root@ip--] # apt install openjdk-11-jre
      
- Check the version

      [root@ip--] # java -version
      
- Install the plugins
 
      [root@ip--] # curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \ /usr/share/keyrings/jenkins-keyring.asc > /dev/null 
  
      [root@ip--] # echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \ https://pkg.jenkins.io/debian binary/ | sudo tee \  /etc/apt/sources.list.d/jenkins.list > /dev/null
  
      
- Update

      [root@ip--] # apt-get update -y
      
- Install the Jenkins

      [root@ip--] # apt-get install jenkins
      
- Configure the permission for Jenkins

      
      [root@ip--] # vi /etc/sudoers
      
      Add the following line in the bottom of file
      press i
      jenkins ALL= NOPASSWD: ALL
      :wq!
      
      
      
-----------------------------------Jenkins-----------------------------------

*Lets Configure Jenkins Now*

- Open Jenkins on web-browser using URL

      URL: http://aws_ip_adress:8080
      
- You will need to to get the token from

      /var/lib/jenkins/secrets/initialAdminpassword
      
- Open EC2-instance again type the given command

      [root@ip--] # cat /var/lib/jenkins/secrets/initialAdminpassword
      
- Copy the text and paste into the jenkins login page you will get jenkins access

- Select Install suggested plugins

- Click on the Dashboard and Create a Job

- Click on the new item

      name - websitedevelopment
      choose - freestyle project
      
- Click on the OK button 

- Click on the job configure

      Description - Website Development with Jenkins freestyle job
      Source code - Git # Paste the Github repository URL
      Branch to build - master to main  # rename
      Build triggers - POLL SCM * * * * *
      
      
     - Build step - Execute Shell
     
                   sudo apt install -y git
                   sudo apt install -y apache2
                   sudo systemctl start apache2
                   sudo systemctl enable apache2
                   suod rm -rf /var/www/html
                   sudo rm -rf /var/www
                   sudo git clone <github repository> /var/www/html
    
    
- Click on apply or save

- Click on Build


*Access the Website*

- Open Browser using URL

      URL: http://<aws_ip_adress>
      
*When the developer do changes in repository code or do the commit with changes. In every commit jenkins will pull the code from github and deploy into the webserver. It will refelct with in a minute it is knows as Continous Integration & Continous Development*


      
      

      
      
      
      
