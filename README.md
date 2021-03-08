# Jam City Club Chat

A serverless web chat built using AWS Lambda, AWS IoT (for WebSockets), SES and Amazon DynamoDB.

The architecture of this application is described in this Google Doc:

- [Jam City Club Chat App Architecture](https://docs.google.com/document/d/1dDcOLEzbkPxe8F148qA3GlMMOTfMTBNsQk4_VwMf8kw/edit)

## Deploying to AWS

A script is provided, `deploy.sh` which uses AWS CloudFormation to provision all the resources needed for this demo. To use it:

- Create an AWS account.
- Visit the [IoT management page](https://console.aws.amazon.com/iot/home) in the AWS web console and ensure that an IoT endpoint has been provisioned for your account.
- Install the [AWS command line tools](https://aws.amazon.com/cli/) and set up your credentials.
- Run the `deploy.sh` script, specifying a name for your new CloudFormation stack, an AWS region and the name of an S3 bucket where the CloudFormation config files will be stored. The S3 bucket will be created if it does not exist.

  ./deploy.sh JamCityClubChatAppStack us-east-1 jamcityappbucket

Once the AWS resources have been provisioned, the script will print a URL to visit in your browser to see the demo.

NB: The Kinesis functionality has been disabled because it is billed per shard-hour. To enable it, edit `cloudformation/template.yaml` and uncomment the relevant lines before running `deploy.sh`.
