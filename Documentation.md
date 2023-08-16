I signed into Tyrone’s Jenkins account and created a new item/pipeline label Nalani_D. Then I went to the ***********Pipeline*********** section and selected Pipeline from SCM since our code and files are coming from Github. I copied my repository link and inputed that into the repository URL box. 

Then I add credentials using my github username and generating a classic token for the password. I changed the branch, applied and saved it.

On my first build, my test failed because I didn’t have the test file uploaded to my repository for it to connect and execute. I recreated my pipeline and it was a success - passing the build and test stages. 

In the console output, Jenkins obtained the Jenkinsfile from Github and used git to download the repository. It then seems to be running packages for python given the “./” After further research it seems that it is checking to see if certain  required packages have been installed.

Then there was a test stage, which created a document with the results.

Then to manually deploy it to AWS Elastic Beanstalk, I download the files from the repository as a zip. I am doing the IAM roles according to the scribe. I created a role for the Elastic Beanstalk and then one for the EC2 - not sure what that is doing  

I then created an application on Elastic Beanstalk. I choose Web Server Environment and titled the application - url shortener. Under platform I selected Python and Python 3.9 running on 64bit Amazon Linux 2023. I am assuming this is the code version in order to run the code. It could also be ensuring to download the dependencies that work together on the python version and operating system. 

When configuring the service access on Elastic Beanstalk we use the role that we previously created. Then we selected the default VPC and selected an availability zone. For the instance type, be sure to delete what the have originally and select the instance that is required

I ran into a server error but it was solved by zipping the actual files instead of using the zipped file from githubI downloaded the files from the C4 deployment and uploaded them to my own repository.
