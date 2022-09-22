# Setting up AWS

### Prerequisite

- Python 3+
- boto3 (pip installable package, do `pip install boto3`)
- An account to AWS Console


### Initial Setup

Go to [AWS](https://aws.amazon.com) and set up your account. Deloitte folks, please do NOT use your company email address when creating your account.

You will be asked to enter credit card information. Please use a personal card. (Don't worry; you won't be charged.)

### Getting the AWS Access Key from IAM

Log into your AWS Console, and select the top right corner, then go to Security Credentials. You'll see the page below.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_1.png">

Create a new access key by pressing the button `Create New Access Key`. A keypair will be automatically generated. 

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_2.png">

Make sure to save your Access Key ID and Secret Access Key somewhere safe, or download to save it. This will be the only time you'll be seeing it.

### Setting up the environment

Create a new file in `~/.aws/credential` on the terminal and paste the details.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_3.png">

Create a new file in ~/.aws/config` and set up the default region.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_4.png">

### Using boto3

Let's try creating a bucket using the boto3 client and your new access key ID and Secret Key.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_5.png">

Open a jupyter notebook or a python console from the terminal.

```
import boto3

s3 = boto3.resource('s3')
s3.create_bucket('your_bucket_name')

# if your region is different than us-east-1,
# you need to specify the region when creating the bucket like in the image

# s3.create_bucket(Bucket='your_bucket_name', 
# CreateBucketConfiguration={'LocationConstraint': 'us-west-1'})
# available regions https://docs.aws.amazon.com/general/latest/gr/s3.html
```
