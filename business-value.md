# Business Value

The organisation found that audiences in Europe were able to access the Tour-de-france API well whereas the North American fans struggled to connect to the application citing poor availability and poor latency. 

By using Docker, Terraform and Ansible - we've been able to quickly create and deploy an application onto Cloud Resources within the space of time to fufill this assessment. 

## Docker
Docker has allowed me to containerise the application and give the team the ability to deploy this quickly to the host environments. We have two microservices:
1. A PostgreSQL DB
2. A Node API (using Express.js)
By Dockerising these two microservices in conjunction with a **docker-compose** file we're able to deploy the two services on any architecture platform using **linux/amd64**. 

## Terraform
Previously if we wanted to deploy resources in a new market (i.e. the USA) we'd have to do serveral things:
- Buy office space in the US
- Buy an on-premesis server
- Configure our server manually
- Deploy application code

Through using Terraform and AWS as a CSP we're able to provision resources in our target market effectively. 
This uses a pay-as-you-go model and we can host the application in the US for as long as neccessary. 

## Ansible
Through a combition of using **Docker** and **Ansible** we're able to create an environment ready to host and run Docker Images through a small series of commands. 

## Overview
With modern day applications it's important for teams to be able to quickly develop and deploy new services. By using micro-services we can increase the cadence of releases for each service by focusing the scope of any one service. This serves us and being able to develop new features and reduce time to market. 

As our infrastructure is created throug Terraform, we also have the benefit using the Declerative Nature of Terraform Syntax and provisioning more servers to suit the demand. 

With working configuration for this application it's easy to bring down a deployment, create new releases and scale the application reducing costs, we can scale the application down during the cycling season and them scale the application up during the Tour de France. 
