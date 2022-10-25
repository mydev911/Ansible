### Create value on aws
- create a file vol.yml
```
- hosts: all
  tasks:
  - ec2_vol
      aws_access_key:
      aws_secret_key:
      volume_size: 10
      device_name: /dev/xvdb
      volume_type: iol
      ips: 100
      zone: us-east-1
      region: us-east-1
      tags:
        Name; Prod_volume
  ```
  ```
  ansible-playbook vol.yml
  ```
  ### Create another playbook to attach this volume to ec2
  - create a playbook file name attach.yml
 ``` 
  - hosts: all
    tasks:
      - ec2_vol
         aws_access_key:
         aws_secret_key:
         instance: id
         volume: id
         device_name: /dev/xvdb
         zone: us-east-1
         region: us-east-1
         delete_on_termination: yes
```
```
  ansible-playbook attach.yml
```
      
   ### Detach volume from ec2
   - create file detach.yml
```
  - hosts: all
    tasks:
      - ec2_vol
         aws_access_key:
         aws_secret_key:
         instance: None
         volume: id
         zone: us-east-1
         region: us-east-1
```
```
  ansible-playbook detach.yml
```
 
   
   
  
