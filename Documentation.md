# Purpose of Deployment
To learn how to use Jenkins to automate the CI pipeline and manually deploy an application on AWS Elastic Beanstalk, which sets up cloud infrastructure concurrently, before learning how to set up each component separately. 

# Steps to Production
## 1. Using Jenkins to build and test application
  ### a. Process
  I signed into Jenkins and created a new item/pipeline label Nalani_D. I connected my Github repository to      Jenkins. Then, I added credentials using my GitHub username and generated a classic token for the password.    I changed the branch, applied, and saved it.
 ### b. Issues
  On my first build, my test failed because I didn’t have the test file uploaded to my repository for it t       connect and execute. I recreated the pipeline, which was a success - passing the build and test stages. 
 ### c. Output
  In the console output, Jenkins obtained the Jenkinsfile from Github and used Git to download the           
  repository. It appeared to be running packages for Python given the “./” However, after further research, i    seems it is checking to see if specific required packages have been installed.
  After, there was a test stage, which created a document with the results.


## 2. Manually Deploy to AWS Elastic Beanstalk
### a. Create IAM roles
 To manually deploy it to AWS Elastic Beanstalk, I downloaded the zipped files from the repository. I created a role for the Elastic Beanstalk and then one for the EC2. The first one allowed Elastic Beanstalk to configure cloud infrastructure for the application, and the EC2 role allows the EC2 instance to use other AWS resources.  
### b. Configure application environment/infrastructure
  I then created an application on Elastic Beanstalk. I chose the Web Server Environment and titled the         application - url shortener. Under the platform section, I selected Python and Python 3.9 running on 64bit     Amazon Linux 2023. I am assuming this is the code version to run the code. It could also be       
  ensuring that the VM has the dependencies that work together on the particular Python version and operating   system. 
  When configuring the service access on Elastic Beanstalk, I used the roles that I previously created.          Then, I selected the default VPC and selected an availability zone. For the instance type, be sure to          delete the pre-selected options and select the required instance.
### c. Issues
  I ran into a server error, which was resolved by zipping the actual files instead of using the zipped          file from GitHub. This is important because the absolute path in the application files is not expecting       to encounter a parent directory, which is created when downloading files from Github.

# CI/CD Pipeline Diagram
![Plan - Deployment 1 drawio](https://github.com/nalDaniels/Deployment1/assets/135375665/3c9087d1-483a-4bf7-866b-3bc1d91a83b4)

# Deployment Success
<img width="906" alt="Screen Shot 2023-08-15 at 9 04 22 PM" src="https://github.com/nalDaniels/Deployment1/assets/135375665/65fd1e9f-dd26-4fd5-91a3-5eb1d47895aa">

