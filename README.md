## Refactor ansible code by importing other playbooks into site.yml



**Step 1 - Jenkins job enhancement**

-  I created a directory in my **Ansible-jenkins** server called **ansible-config-artifact**

![Alt text](<images/Unsaved Image 2.jpg>)



-  I changed permissions to this directory using **chmod -R 0777 /home/ubuntu/ansible-config-artifact**, so Jenkins could save files there. I also changed permission on the parents directory /home/ubuntu and added jenkins to ubuntu user. 

-  In jenkins web console, i searched for **copy artifact** plugin and downloaded it. 


![Alt text](<images/Unsaved Image 3.jpg>)


-  I created a freestyle project called **save_artifacts** and configured the build steps to copy artifact from from my Ansible project to my newly created folder **ansible-config-artifact**
![Alt text](<images/Unsaved Image 4.jpg>)


- I made change to my readme.md folder to confirm that that my build step in **save-artifact** project will be trigared and copy artifact to **ansible-config-artifact** folder


![Alt text](<images/Unsaved Image5.jpg>)


- I also confirmed that the artifact was copied to my **ansible-config-artifact** folder


![Alt text](<images/Unsaved Image6.jpg>)


## Step 2 - Refactor Ansible code by importing other playbooks into site.yml

-  I created a new branch in my ansible-config-mgt called refactor 

  ![Alt text](<images/Unsaved Image7.jpg>)


  -  i created a file in my playbook called site.yml and also created a folder called **static-assignment** in my root folder. I moved common.yml to my **static-assigmnet** folder and then inported **common.yml** playbook into **site.yml**.

  ![Alt text](<images/Unsaved Image8.jpg>)



  -  Run **ansible-playbook command** against the dev environment

  I created a folder called del-common.yml and updated site.yml with it to delete wireshak in my servers 


![Alt text](<images/Unsaved Image 9.jpg>)

-  I ran the playbook to delete wireshark  as **ubuntu@ip-172-31-94-81:~/ansible-config-artifact$ ansible-playbook -i inventory/dev.yml playbooks/site.yml**  and it was successful 




![Alt text](<images/Unsaved Image 10.jpg>)


-  I also ssh into my 4 servers to confirm wireshak was deleted.


![Alt text](<images/Unsaved Image11.jpg>)


## Configure uat webservers with a role webserver


## Step 3 - Configure UAT Webservers with a role 'Webserver'

 - I spined up 2 rhel 8 instances in aws called web1 and web2


  