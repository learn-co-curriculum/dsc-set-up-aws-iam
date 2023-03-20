# AWS Access Keys, boto3, and Making Buckets


### Initial Setup

You will have had to completed the previous assignment called "AWS Sign Up"

### Objectives

At the end of this assignment, you'll have AWS security access keys so that you can give various programs permission to interact directly with the AWS servers. Think of this as setting up a secure sign in. The steps below will allow you to generate a specific code that you can store on your machine and have your programs use to let AWS know that it really is 'you' attempting to access AWS resources. 

Additionally, we'll install and test boto3, which is the library maintained by AWS in order to allow Python users deeper ways to interact with AWS tools. [You can find more details in the Boto3 documentation page here.](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) We'll use boto in a jupyter notebook to create a 'bucket' that we can later use to store data.  

### Getting the AWS Access Key from IAM

First, we need to have AWS generate the credentials we need. First, open your internet browser and navigate to https://aws.amazon.com/console/. Make sure that you are logged into the AWS account you set up earlier.  Then open up Security Credentials. You should find that in the top right corner, under 'My Account'. You may need to re-enter your login and password. Once you've done that, scroll down to the section called 'Access Keys'. You may need to click through a screen encouraging you to use IAM account, ignore this for now. 

You should see something like the image below:

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_1.png">

Create a new access key by pressing the button `Create New Access Key` as seen below. 

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_2.png">

This will generate a keypair for you automatically. If you are interested in cryptography understanding how a keypair works is critical, but for our purposes we can think of a keypair like a password that is on one hand *much* harder to crack than the usual 'password123' type of password. The downside is that it is just a jumble of pseudo-random information that is much harder for humans to remember. So we'll copy and paste it into a secure location, and try to not rely on these keys for too much, because if someone is able to compromise your computer, they'd also get access to whatever access level you grant these keys in your AWS account. This is part of why we won't be putting 'real' data into any of our AWS practice tasks!

Copy and paste the keys into a safe place on your computer. Alternitively, you can press the download button to save the two keys as a csv file. This will be the only time you'll be seeing them. 

{Julian note: if we're not doing the Amazon CLI I'm not sure how this keypair will actually be integrated. It's possible this whole page won't work without  AWS CLI, in which case we might need alternate lessons? Not sure how to set up buckets without an authorized account.}

### Setting up the environment

{Julian's note: not sure what the replacement step is here...}

Create a new file in '~/.aws/credential' on the terminal and paste the details.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_3.png">

Create a new file in '~/.aws/config' and set up the default region.

<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_4.png">

### Using boto3a

Let's try creating a bucket using the boto3 client and your new access key ID and Secret Key.

{Julian's note: I think this image is too confusing/intimidating for students. I recommend cutting it.}
<img src="https://raw.githubusercontent.com/learn-co-curriculum/dsc-set-up-aws-iam/main/assets/aws_access_5.png">

Open a jupyter notebook from the terminal, and run these commands in the cell. You will need to name your bucket and you will need to set your region. You can learn more about that by reading the information [here](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

```
import boto3

s3 = boto3.resource('s3')

s3.create_bucket(Bucket='<your_bucket_name>', 
                CreateBucketConfiguration={'LocationConstraint': '<your region here>'})
                
```


