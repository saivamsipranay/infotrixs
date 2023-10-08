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
-	Lets start with Creating a security group for monolith server
-	Goto AWS console and search for security groups  
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/76575462-8d6e-44ef-b5ff-346b4398a7ef)
-	Click on create security group and Fill the details
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/a064c1bf-acb2-4367-a1ab-f9f3edf7568f)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/66c03304-b785-440f-825c-b2264fc62641)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/b1c40763-b0d5-45ac-8958-b065da6a5139)
-	Click create security group. It will create a sg.

-	Now go to EC2 and Click Launch instance 
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/2a8859a0-f60e-4e39-bf54-af31ba417d8e)
-	Now give a name for instance, select the ubuntu AMI and t2.micro instance type
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/314c0c20-3d9b-447f-aa7b-76ce636caf0e)
