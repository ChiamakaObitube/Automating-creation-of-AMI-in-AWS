# Automating-creation-of-AMI-in-AWS

## Prerequisites

1. AWS account
2. Knowledge of Git/Github
3. Bash
4. Packer
5. Ansible

## Steps

**Install Packer**
### On Ubuntu

* curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
* sudo apt-add-repository “deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main”
* sudo apt-get update && sudo apt-get install packer

### Mac OS
* brew install hashicorp/tap/packer

### Windows if you are using Chocolatey
* choco install packer

**Install Ansible**
### Ubuntu
* sudo apt update
* sudo apt install software-properties-common
* sudo apt-add-repository --yes --update ppa:ansible/ansible
* sudo apt install ansible

**Create AWS Environment Variables**

Create a directory in your local computer and cd into it. Inside this directory, create a .env file that will contain your AWS access key id and secret key and region.
```
   export AWS_ACCESS_KEY_ID=
   export AWS_SECRET_ACCESS_KEY=
   export AWS_REGION=
```
