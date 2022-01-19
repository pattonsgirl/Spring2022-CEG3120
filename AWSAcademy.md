# Getting Started with AWS Academy

1. Open email from AWS Academy to accept invite to course.
   - Email your course instructor if you did not recieve an email.
2. You will be joined to a Canvas course called AWS Academy Learner Lab - Foundation Services
   - If you are in multiple courses using AWS, you may need to get used to the "Dashboard" to spend funds in the correct course.
3. Within the course, click **Modules**
4. Click **Learner Lab - Foundational Services**
5. Click the **Start Lab** Play button on the middle right
6. Wait. 2 - 3 minutes. You will see a console appear that you can interact with.
   - This terminal is configured with AWS CLI access - you can query resources created on your account with it, but in itself is not what we are aiming for. Proceed with next instructions.
7. Click **AWS Details** (with info icon next to it). Click download PEM from the SSH key options
   - You'll need this for Connecting to the AWS Environment (below)
8. Click **AWS** which should have a green dot next to it located on the left
   - This will take you to your AWS Console for your account. Now the fun begins.
9. In a new tab, enter the following URL in the browser (or click link to open): https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ceg2350&templateURL=https:%2F%2Fwsu-cecs-cf-templates.s3.us-east-2.amazonaws.com%2Fcourse-templates%2Fceg2350.yml

   - On the first menu, click Next
   - On the second menu, under Parameters, under Key Name, select `vockey`
   - Click Next
   - On the third menu, select Next
   - Scroll to the bottom and select Create Stack
   - You will be redirected to a status page that says CREATE_IN_PROGRESS

10. Once you have created the AWS Cloud formation stack you can [return to the EC2 service](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Home:).  
    Here you should see additional resources have been created (not everything says 0 anymore)
11. Click on [Running Instances](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceState)
12. Our machine should now be created (or almost ready).
13. Your machine will be assigned an Elastic IP address, which you can view by clicking the check mark next to the instance listing. This IP address is what we will use to SSH into the virtual environment.

**WARNING**
While exploring and discovery is an important part of this course, any additional resources you create in AWS have an associated charge. If resources besides those strictly asked for by this course stay running, you risk running out of funds for this course. While fixable, this will hinder your ability to complete projects on time.

## Connecting to the AWS environment

**You are now ready to make an SSH connection to your AWS server.**

- Open a terminal.
- Copy the AWS SSH key that was downloaded to your system to your home directory in your terminal
  - Helpful commands: `cp, ls, man`
  - The manual method: Create a file with a useful name (or the same name as the downloaded file) `ceg3120-aws-vm.pem`
  - Open a text editor (`vim` or `nano`)
  - Copy and paste the contents of the key that was downloaded from AWS Educate into the file.
- Change the permissions on the key file in your directory
  - Because private keys need to be protected, the key needs to be changed to readable by your user by using `chmod`
  - `chmod 600 /path/to/private/key` - replace _/path/to/private/key_ with your information
  - Resource on how to use [chmod](https://www.howtogeek.com/437958/how-to-use-the-chmod-command-on-linux/)
- SSH into your AWS server with the following command  
   `ssh -i /path/to/private/key ubuntu@ElasticIP`  
   Note: replace _/path/to/private/key_ and _ElasticIP_ with your information
  - If your connection was refused, you may have forgotten to put the username `ubuntu` in front of your Elastic IP address
- You are now signed in to your AWS Educate system as the user `ubuntu`

# On-going Notes

- Important notes:
  - Sessions last 4 hours. Session time can be refreshed. Instances spin down after 4 hours
  - Budget cannot exceed $100 - account will vaporize - all resources created by account will be deleted
