# 4640-pod1
# Ansible Setup for AWS
# 1. Create a Repo named 4640-pod1 on github and clone it to home directory.
# 2. Create a ansible.cfg file in directory 4640-pod1
# 3. Add the following to ansible.cfg file:
```
[defaults]
inventory = inventory

[inventory]
enabled_plugins = ini 
```
# 4. After that create 2 VM's on AWS ec2. First one will be Ubuntu 22.04 and second one will be Rocky 8.
# 5. Create a access key for both the VM using AWS web console go to the IAM(Identity access management) dashboard. Create a new group naming BCIT_4640 Give the new group AdministratorAccess under Attach permissions policies - Optional. 
# 6. Create a new User on AWS. In the Users tab .Give your user programmatic access and provide user with permission from group BCIT_4640. This will generate a access key and access secret. Download the csv. 
# 7. copy and paste the access key and access secret in .profile (located in home directory) by using ```
vim .profile ``` 
# and paste the acccess key and id on the bottom like and then save it.  
```
export AWS_ACCESS_KEY_ID = 
export AWS_SECRET_ACCESS_KEY =
```
# 8. After that use ```source .profile ``` Test it using ```echo $AWS_ACCESS_KEY_ID ``` 
# 9. Create a inventory directory in 4640-pod1. cd into inventory and create  1 files named hosts.aws_ec2.yml for aws users. 
# 10. In hosts.aws_ec2.yml file add as shown in below. 
```
---
plugin: aws_ec2
regions:
    - us-west-2
```
# 11. test the setup up by pinging using ``` ansible -m ping -u root all ```
# 12. upon completing the setup use ``` ansible inventory --graph ``` to check the connection. 
![4640-graph](https://user-images.githubusercontent.com/78824700/198678290-173fbc13-137e-4586-9a29-6da7051d5254.JPG)
