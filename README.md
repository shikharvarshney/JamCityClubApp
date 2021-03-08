
# Jam City Club Chat

A serverless web chat built using AWS Lambda, AWS IoT (for WebSockets), SES and Amazon DynamoDB.

The architecture of this application is described in this Google Doc:

- [Jam City Club Chat App Architecture](https://varshneyyshikhar.s3.amazonaws.com/Project+proposal.pdf)


### Prerequisites

What things you need to install the software and how to install them

```

Software	          Version

Node Js	                >= 12.0
NPM	                    >= 6.0.0
Homebrew                Install the latest one
Yarn                    It is a good practice to install yarn instead of NPM
aws-cli                 Latest version
Any Editor of your      Latest Version
Choice. Preferably 
VSCode
```

## What all is there in this template?

```Components deployed in the App``` are:-

1. ```AWS S3``` for hosting the website. I have not used Cloudfront for now. But it can be easily 
2. ```AWS Cognito Identity Pool``` and an Id is created for each user who sends a message.
3.  `AWS DynamoDB` with Chat table and Club Name or Room Name( I initially coded for rooms and then remembered to use Clubs as per the problem statement) is the partition key for this system.
4. ```AWS Lambda``` for basic chat implementation with the Trigger of AWS-IoT rules.
5. ```IoT Rules``` explained in the architecture document.
6. ```AWS-IoT Endpoint``` must be enabled for the region in which you are deploying your code.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

## Deploying to AWS

A script is provided, `deploy.sh` which uses AWS CloudFormation to provision all the resources needed for this demo. To use it:

- Create an AWS account.
- Visit the [IoT management page](https://console.aws.amazon.com/iot/home) in the AWS web console and ensure that an IoT endpoint has been provisioned for your account.
- Install the [AWS command line tools](https://aws.amazon.com/cli/) and set up your credentials.
- Run the `deploy.sh` script, specifying a name for your new CloudFormation stack, an AWS region and the name of an S3 bucket where the CloudFormation config files will be stored. The S3 bucket will be created if it does not exist.

  ./deploy.sh JamCityClubChatAppStack us-east-1 jamcityappbucket

Once the AWS resources have been provisioned, the script will print a URL to visit in your browser to see the demo.

Before using this app:- ```You have to add your email Ids on SES console since I have not used a verified domain for this app. This will facilitate you to send emails to the people without a verified domain and test my functionality of inviting users to the Club.```

NB: The Kinesis functionality has been disabled because it is billed per shard-hour. To enable it, edit `cloudformation/template.yaml` and uncomment the relevant lines before running `deploy.sh`.

## Contributors
* **Shikhar Varshney**
