# aws_credentials

## Description:

Manages the AWS `~/.aws/config`config file for the cli as follows:
- Variable `arg_action` is not defined or is defined and set to `create`: create the config file
- Variable `arg_action` is defined and is set to `delete`: delete the config file


## Behaviour:

**Feature:** Create or delete `~/.aws/config` file  
- **Given** valid AWS credentials exist
- **When** the playbook is executed 
- **Then** the config file is created when `arg_action` is not defined or is defined and not set to `delete`
- **Then** the config file is deleted when `arg_action` is defined and is set to `delete`

## Configuration:

Common variables used by this role:

| Variable | Description | Example |
|-----|-----|-----|
| **aws_region** | AWS region | See [AWS regions](http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region) |
| **aws_access_key** | AWS access key | AKIAIOSFODNN7EXAMPLE |
| **aws_secret_key** | AWS secret key | wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY |
| **arg_action** | Used to create or delete `config` file | undefined, `delete` or `create` |

## Usage:

How to invoke the role from a playbook (create config file):

```yaml
- name: Creating the AWS config file
  include_role:
    name: aws_credentials
  vars:
    aws_access_key: "AWS-ACCESS-KEY"
    aws_secret_key: "AWS-SECRET-KEY"
    aws_region: "eu-west-2"
```

How to invoke the role from a playbook (delete config file):

```yaml
- name: Deleting the AWS config file
  include_role:
    name: aws_credentials
  vars:
    aws_access_key: "AWS-ACCESS-KEY"
    aws_secret_key: "AWS-SECRET-KEY"
    aws_region: "eu-west-2"
    arg_action: "delete"
```
