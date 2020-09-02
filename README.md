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

Create a directory in your local computer and cd into it. Inside this directory, create a .env file that will contain your AWS access key id and secret key and region. Add the file to the.gitignore to avoid getting pushed to the remote repository.
```
   export AWS_ACCESS_KEY_ID=
   export AWS_SECRET_ACCESS_KEY=
   export AWS_REGION=
```
## Build Custom Image 

* **template.json** file is a customized Packer template that creates the machine image using the configurqations specified.
* **ansible_playbook.yml** performs different tasks which will set up a NodeJs web app including all dependencies, configure an Nginx proxy server to make the app available to the internet, setup pm2 to make the application always available even when the instance is restarted.

* Run `bash build_image.sh` to provision the image.

## Launch EC2 Instance using the newly provisioned AMI

* Navigate to the EC2 dashboard our new AMI will be listed in the main window of the Images -> AMIs section.
* Launch an EC2 instance using the newly created AMI as our image. 
* Click on Launch and create a security group that will allow traffic from all sources via the port 3000.
* Choose a new or existing key pair and launch the instance.
* Copy the public IP address of the instance and paste on the browser.

## Further readings

* Read up on Medium [Building Custom AMI image using Ansible and Packer](https://medium.com/@chiamakaobitube/building-custom-machine-image-using-ansible-packer-and-bash-in-aws-178b93d08136)

