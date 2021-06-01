# Building a search application with Amazon ElasticSearch

Description

## Requirements

* **AWS Account:** If you don’t have an account nor an account provided to you, [click here](https://aws.amazon.com/es/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc).
* **Text editor (optional):** Just to make things easier and more organised.

## Architecture

ARCHITECTURE IMAGE AND EXPLANATION (coming soon)

## Launch the template

1. Deploy the AWS Cloud Formation template clicking on the button below:

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
aws cloudformation create-stack --stack-name $STACKNAME --template-url https://elastic-search-movies-search-app.s3-eu-west-1.amazonaws.com/Templates/main_es.yaml --tags Key=project,Value=glue-project --profile $AWSPROFILE --region=$AWSREGION --capabilities CAPABILITY_IAM
```
*NOTE*: The template takes 30 min to deploy approx.

## Explore your environment

(Coming soon)

## Final Step

Once your CloudFormation template is deployed, go to AWS Lambda service on the console, and choose the one with the name **YourStackName-Lambda-RandomString-searchlambdacf-RandomString**. On the configuration tab, select Triggers > Add Trigger. From the list click on API Gateway > Select the one with the name **search-es-api**. For deployment stage select search-es-api-tetst and for the Security option, select Open and then click Add:
  
![trigger](/Images/trigger.png)

And that's it!! You're rady to test your application. 

# Test your movies search app

Look for the Amazon S3 static website endpoint. Go to CloudFormation, select the recently launched template, specificly click on the nested one called **YourStackName-Lambda-RandomString** and click on the Outputs tab. You'll see WebsiteURL with a link like **http: //search-app-accountID-.s3-website-eu-west-1.amazonaws.com/**. Once opened, a static website like this will appear: 

![sample-site](Images/sample-site.png)

Now, type the item to search for! For example, "Thor"

![thor](/Images/thor.png)

Cheers!!

## Authors

* Daniel Neri
* Serhat Gülbetekin

