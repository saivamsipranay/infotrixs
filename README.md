# infotrixs
Cloud Intern (AWS) Report

Task: Deploy application in monolithic and microservices architecture
❖ Description:
- For monolithic: 1 EC2 instance, deploy WordPress and MYSQL on the same instances
- For microservices: 2 EC2 instance, 1 for WordPress and 1 for MYSQL
- Configure the necessary security group for the instances
- EC2 instance type: t2-micro, AMI: ubuntu-*
❖ Create a welcome page in WordPress that will be the homepage
❖ Goal to this task to check your understanding level
❖ Create a video and report of how you completed it with proper screenshots

Monolithic: 
1.	Create a EC2 instance with Ubuntu OS
-	Create a security group for monolith server   
-	Add Inbound rules 
 

-	Click create security group. It will create a sg.

-	Now go to EC2 and Click Launch instance 
 
-	Now give a name for instance, select the ubuntu AMI and t2.micro instance type 
 
-	Create a key pair and select the sg that we created earlier
  ![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/d3d48429-6571-40b1-bbbb-f19cec06d53f)

 
-	Now hit the Launch instance, A instance will create.
 
-	Now log in to the monolithic instance using ssh
 

