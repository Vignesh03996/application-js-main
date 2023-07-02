# application-js

Task 01:
We create the infrastructure using the terraform i have upload all the terraform file in one single file along with all screen shots
In task one we create infra using terraform and use s3 bucket as backend to store tfstatefile

Task 02:
We create the load balancer with target groups for jenkins and app server traffic for alb_dns/jenkins we have configure in target group and same has been done on jenkins
server in service file and trafic with only alb_dns is sent to app server
we store all creds in jenkins manage cred along with git/aws creds and private key for ssh
we ceate private ECR repo for image push and pull 
we create inventory file for installing docker into jenkins and app server, we write the playbook file and we use shell script to install docker on servers
we write script and copy that script into jenkins and app and run that script using ansible playbook

Task 03:
We have created the Dockerfile and it succesully works we write the jenkisfile and that to sucessfully works 
i have attached the screenshots and github repo link in task 03 folder


