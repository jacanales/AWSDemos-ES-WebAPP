# Building a search application with Amazon ElasticSearch

Description

## Requirements

* **AWS Account:** If you don’t have an account nor an account provided to you, [click here](https://aws.amazon.com/es/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc).
* **Text editor (optional):** Just to make things easier and more organised.

## Architecture

ARCHITECTURE IMAGE AND EXPLANATION (coming soon)

## Launch the template

1. Go to Amazon EC2 Console and on the left pane click on *Key Pairs* and create a key pair called **ESKeyPair**. Choose the .pem format and create the key pair.

![Key_Pair](/images/KeyPair.png)

2. Deploy the AWS Cloud Formation template clicking on the button below:

[![Launch CFN stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://eu-west-1.console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/quickcreate?templateUrl=https://elastic-search-movies-search-app.s3-eu-west-1.amazonaws.com/Templates/main_es.yaml&stackName=search-app)

**(Optional)** Or deploy the template with CLI:

* If you don’t have the AWS CLI installed, follow [these](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) steps. And to configure the AWS CLI, follow [these](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-config). 
* Clone the repository.
* Export the following parameters in your CLI:
```bash 
export AWSREGION=<YOUR AWS REGION>
export AWSPROFILE=<YOUR AWS PROFILE>
export STACKNAME=<THE NAME OF YOUR STACK>
```
* Go back to your terminal and create the CloudFormation stack:
```bash
aws cloudformation create-stack --stack-name $STACKNAME --template-url https://aws-glue-with-s2s-vpn.s3.amazonaws.com/Templates/main.yaml --tags Key=project,Value=glue-project --profile $AWSPROFILE --region=$AWSREGION --capabilities CAPABILITY_IAM
```
*NOTE*: The template takes 30 min to deploy approx.

## Explore your environment

(Coming soon)

## Final Step

Once your CloudFormation template is deployed, go to AWS Lambda service on the console, and choose the one with the name <Your Stack Name>-Lambda-<Random String>-searchlambdacf-<Random String>. On the configuration tab, select Triggers > Add Trigger. From the list click on API Gateway > Select the one with the name search-es-api-cf. For deployment stage select search-es-api-tetst and for the Security option, select Open and then click Add:
  
  PIC

And that's it!! You're rady to test your application. 

#Test your movies search app

Look for the Amazon S3 static website endpoint. Go to CloudFormation, select the recently launched template, specificly click on the nested one called <Your Stack Name>-Lambda-<Random String> and click on the Outputs tab. You'll see WebsiteURL with a link like http://search-app-<accoundID>.s3-website-eu-west-1.amazonaws.com/. Once opened, a static website like this will appear: 

Cheers!!

## Authors

* Daniel Neri
* Serhat Gülbetekin

