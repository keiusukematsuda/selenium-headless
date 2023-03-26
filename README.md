# About This Repository

In order to run Selenium with Lambda, there are many things that must be prepared, so it's difficult.

Here is a summary of the procedures for efficiently running Selenium programs with Lambda.

## things to do

- Lambda to run Selenium in Headless mode
- IaC (Infrastructure as Code) using AWS SAM
- Make it easy to test locally (Selenium Headful mode)

# Reference

https://qiita.com/K5K/items/1180f73d7e3e74493a40

# How To Use 

## Prerequision


- Installed these packeges on your labtop(Mac  Monterey ver 12)
  - [Google Chrome Browser](https://support.google.com/chrome/answer/95346?hl=ja&co=GENIE.Platform%3DDesktop) 
  - python3(3.7 recommended)
  - [SAM CLI](https://docs.aws.amazon.com/ja_jp/serverless-application-model/latest/developerguide/install-sam-cli.html)
- Available AWS Account and Credential (to use aws cli)


## Procedure


### Clone Repository 

```
❯ git clone https://github.com/keiusukematsuda/selenium-headless.git

❯ cd selenium-headless
```

### Create Virtual Env


```
❯ python --version
Python 3.7.10

❯ python -m venv .env

.env ❯ pip install -r requirements.txt
```


### Execute Selenium Script at Local

```
.env ❯ cd selenium-headless/function/selenium-headless
```

```
.env ❯ python lambda_function.py

# if the result as below, The Script was succeeded
Google
```

### Create Lambda Function and Others

```
.env ❯ cd ../..
.env ❯ ls
function/	layer/		template.yaml
```

```
.env ❯ sam build
```

```
.env ❯ sam deploy --guided

	Setting default arguments for 'sam deploy'
	=========================================
	Stack Name [sam-app]: sample-selenium-headless
	AWS Region [ap-northeast-1]: ap-northeast-1
	#Shows you resources changes to be deployed and require a 'Y' to initiate deploy
	Confirm changes before deploy [y/N]: y
	#SAM needs permission to be able to create roles to connect to the resources in your template
	Allow SAM CLI IAM role creation [Y/n]: Y
	#Preserves the state of previously provisioned resources when an operation fails
	Disable rollback [y/N]: N
	Save arguments to configuration file [Y/n]: Y
	SAM configuration file [samconfig.toml]:samconfig.toml
	SAM configuration environment [default]: default


.....


Previewing CloudFormation changeset before deployment
======================================================
Deploy this changeset? [y/N]: y
```

### Check Lambda Function

Login your AWS Account.
And, Execute Lambda Function (you deployed)


