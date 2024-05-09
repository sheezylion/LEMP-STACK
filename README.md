# LEMP STACK DOCUMENTATION
![LEMP STACK](https://github.com/sheezylion/LEMP-STACK/assets/142250556/8f56b168-dd72-4416-9dc7-2e84b29b4fa7)

## WHAT IS LEMP STACK
LEMP is an open source web-application stack used to develop web applications. The term LEMP is an acronym that represents:
- L - Linux operating system
- E - Nginx server (Pronounced as engine-x, hence the E is acronym)
- M - Mysql database
- P - Php for scripting langiage


LEMP enjoys community support, hence it is used around the world in many highly scaled web applications. Nginx is the secind most widely used web server in the world following apache.

## HOW LEMP STACK WORLS
The LEMP stack works by using nginx web server, which listens for HTTP request and forward it to the appropriate php script. The php script generate a response which is then sent back to the user via nginx.
Mysql is used to store and manage the website data. Php communicate with mysql to retrieve and store data as needed.

## WHY LEMP STACK IS POPULAR IN WEB DEVELOPMENT
- High performance 
- Scalability
- Open-source
- Security

## Disaavantages of LEMP
- If configurations are considered Nginx does not allow additional configurations which is a downside unlike Apache as it is more flexible in this case.
- Not flexible enough to support dynamic modules and loading.

## Prerequisites
In order to install nginx web-server, mysql database and php, we need to first launch a server in AWS using EC2 instance.

## How to launch an EC2 instance server on AWS
To get started search EC2 in your AWS console, click on launch instance to create an instance and name the requirement

<img width="1401" alt="1" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/47909bef-7054-4998-b47a-03e3ccf72ca1">

Step 1: Once you click on launch instance, the next thing is to name your server and choose your preferred Amazon machine image AMI, we would select ubuntu 24.04 LTS free tier

<img width="803" alt="2" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/511dcd02-a312-4a22-b622-db95cdb6cdee">

Step 2: Choose instance type, select t2.micro, then select key pair. if you don't have one created before or select an existing one. I have created one before, so i would select it.

<img width="804" alt="3" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/f8a51c81-9b52-4406-b974-d812afe58408">

Step 3: Select create a security group, ssh traffic on port 22 has been allowed by default, you can choose to disallow but in our case we want to ssh into our server from the terminal, so we would allow. Also select allow HTTPS traffic and HTTP traffic from the internet. 

<img width="793" alt="4" src="https://github.com/sheezylion/LEMP-STACK/assets/142250556/4936cb06-af95-466e-bff9-effcc3e3143d">





