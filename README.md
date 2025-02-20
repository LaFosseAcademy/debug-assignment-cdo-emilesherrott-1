# Debug Assignment CDO

## Project Overview
This application is designed to configure two microservices to run on AWS resources in North America to bring information about the TdF cyclists to a new audience. 

## Terraform Scripts
- **Terraform** is used in this project to provision an EC2 Instance to host the application in North Virginia using the AWS region `us-east-1`.
- If trying to launch this application for the first time you'll need to have a:
  - `AWS account`
  - `AWS IAM user` - with admin rights to create resources and also the **access key** and **secret access key** stored as environment variables. 
- `terraform init` - to access the correct Terraform plugins for AWS
- `terraform apply` - to provision the resources defined in the **tf** files. 
- Use either **known state** or **AWS GUI** to find the IPv4 address for use in **ansible** later. 

## Transfer docker-compose.yml to EC2

Use either `scp` to securly copy the `docker-compose.yml` file over the the EC2 instance or manually `ssh` into EC2 instance and configure manually using `nano`. 

- Example of `scp`: `scp -i <identity-file-location> <file-to-send-to-instance> <remote-username>@<ip-or-dns-of-instnace>:/<path-to-copy-to>`

## Ansible
Ansible is used to configure the pre-existing infrastructure for this application. You'll need to the IP address for the cloud server to run this playbooks on. 
- Inside `ansible_hosts` add the running EC2 instance's IP address as a mananged ansible node. 
- From the location of `ansible.cfg` execute two more ansible commands. 
  - `ansible-playbook playbooks/docker-install.yml` to install docker and docker-compose to EC2 instance. 
  - `ansible-playbook playbooks/docker-run.yml` to run the docker-compose file on the instance. 

## Access the deployed application

Visit the IP address or DNS using the port of `:3000`
- i.e. `<ip-address>:3000/`

## Bugs
- No known bugs

## Following usages
- Remember to delete to resources used to create this application: from **/terraform**, run: `terraform destroy`