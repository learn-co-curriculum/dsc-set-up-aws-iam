# Setting up AWS

### Prerequisite

- Python 3+
- boto3 (pip installable package, do `pip install boto3`)
- An account to AWS Console


### Getting the AWS Access Key from IAM

Log into your AWS Console, and select the top right corner, then go to Security Credentials. You'll see the page below.

![aws_access_1](./assets/aws_access_1.png)

Create a new access key by pressing the button `Create New Access Key`. A keypair will be automatically generated. 

![aws_access_2](./assets/aws_access_2.png)

Make sure to save your Access Key ID and Secret Access Key somewhere save, or download to save it. This will be the only time you'll be seeing it.

### Setting up the environment

Create a new file in `~/.aws/credential` on terminal and paste the details.

![aws_access_3](./assets/aws_access_3.png)

Create a new file in ~/.aws/config` and set up the default region.

![aws_access_4](./assets/aws_access_4.png)

