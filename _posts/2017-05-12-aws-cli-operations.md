---
layout: post
title:  "AWS CLI Operations"
date:   2017-04-22 17:12:08 +0530
categories: aws
tags: aws cli awscli
---
#### Interested in checking out [Installing](https://jningtho.github.io/aws/walkthrough-aws-cli-tool/) `awscli`*

<img src="/assets/img/aws-shell.png">

So I have installed `awscli` tool on my macbook or ubuntu. Now what? Where do I go from here. If you've reached this far I'd be wrong to say that you have not created a [FREE TIER](https://aws.amazon.com/free/) account in AWS and are anxious to hop on the bandwagon. Say no more!

### Checklist
* You have created a FREE TIER account in aws
* You have logged in as the root user
* You have also created a _new user_ and have attached _AdministratorAccess policy_.
* Ensure you are logged in a the _new user_ above at all times for all your administrative tasks and not the _root user_.
* Make sure you have completed all the 5 listed tasks on the Identity and Access Management dashboard before proceeding with any activity within your AWS Account.

<img src="/assets/img/iam-todo.png">

NOTE: Please make sure to follow _IAM Best Practices_. You may see the [aws  documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users).

### Configuring CLI Profile:
You have _new user_ created, and the Secret Access Key and Secret ID are downloaded safe. *NOTE:* This is generated only once, the first time you create a new user. Should you lose this information, you have no way of retrieving it BUT to only generate a new set of keys and make the previous set 'inactive'. You'd now like to configure your AWS profile. Run the following command in your terminal.


#### Configuring with static variable
* Scenario 1: You are managing/working on a single AWS Account

```shell
$ aws configure
AWS Access Key ID [****************35LQ]: <enter your Access Key ID here>
AWS Secret Access Key [****************ddwk]: <enter your secret Access key here>
Default region name [us-east-1]: <enter your default region>
Default output format [json]: <leave this blank, will default to json>
```

* Scenario 2: You have multiple AWS Accounts for multiple customers to manage and you need to configure the static profiles on your laptop/machine, run the command with the `--profile <profile-name>` flag like so for every profile (account).

```shell
$ aws configure --profile profile1
AWS Access Key ID [****************35LQ]: <enter your Access Key ID for profile1>
AWS Secret Access Key [****************ddwk]: <enter your secret Access key here>
Default region name [us-east-1]: <enter your default region>
Default output format [json]: <leave this blank, will default to json>
```

Once completed, you should be able to see a hidden folder `~/.aws` within your user profile in your machine with 2 files.
* config - will have the profile (or different profiles) information with the region and the output format as defined when the profile was configured.
* credentials - will have the profile information, Access Key Id and the secret Access key.

NOTE: It is extremely imperative that these information are kept in a safe location away from prying eyes. If someone should accidentally get hold of your Administrative access to your AWS account, perhaps you might be aware that a million  dollar company got shut down overnight. Please google up for information.


#### Configure environment variable for an authenticated user (temporary)
Here's another method to allow temporary CLI access to your account.

```shell
$ export AWS_ACCESS_KEY_keyID
$ export AWS_SECRET_KEY_key
```

#### Testing if the CLI authentication works with a simple command

```shell
$ aws ec2 describe-instances --region us-east-1
```
#### Revoming access to environment variables

```shell
$ unset AWS_ACCESS_KEY_keyID
$ unset AWS_SECRET_KEY_key
```

#### List current configured profile

List the AWS CLI current configuration data. This command will show you the current configuration data. For each configuration item, it will show you the value, where the configuration value was retrieved, and the configuration variable name. For example, if you provide the AWS region in an environment variable, this command will show you the name of the region you've configured, it will tell you that this value came from an environment variable, and it will tell you the name of the environment variable.

```shell
$ aws configure list
Name                    Value             Type    Location
    ----                    -----             ----    --------
 profile                <not set>             None    None
access_key     ****************35LQ shared-credentials-file    
secret_key     ****************ddwk shared-credentials-file    
  region               ap-south-1      config-file    ~/.aws/config
```

#### Review your configuration for a specific profile?

```shell
$ aws configure list --profile profile-name
```

You should now be confident and ready to venture out into the `awscli` world on your own. It is important that you familiarize yourself with the services and the arguments required for different tasks and activity. AWS has provided a very well documented and elaborate `user reference guide` [here](https://docs.aws.amazon.com/cli/latest/reference/).

Happy Learning and stay cool!
