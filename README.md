# CI-CD-Pipeline-using-jenkins-docker-and-ansible
#Project-Idea

I have created a CI/CD Pipeline where a war-file is build from maven project and created a tomcat container and deployed the webapp on the tomcat container
using Jenkins, Maven, Ansible and Docker with the help of Dockerfile and Ansible-Playbok by integrating them with each other.
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *


#Objective_of_Project


1)This project gives automation where continuous delivery will allow the software to add new features and go live at any stage
2)It will also remove human errors and will need not to do manual things like stopping and deleting the existing docker-container and images while some changes are made on github code repo
3)In future it can also be deployed on kubernetes to make it scalable and we can also add replicas so that the if the container goes down for any reason the webapp should not face downtime.

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

#PROJECT_OVERVIEW
<img width="1023" alt="overview" src="https://user-images.githubusercontent.com/95365748/191949125-797f31bf-b639-47a7-b27a-2fb898f9d4bb.png">



* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
#Jenkins-Role:-


jenkins should pull the code from github and using pom.xml file it should create a war-file of the maven project.


* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 





#Ansible-Role:-


ansible-server should run playbook1.yaml on itself to create docker-image and tag it and then push it to dockerhub
also ansible-server should run playbook2.yaml on docker-server to stop and delete the existing container and image so that it should not give error like container and images are already present and need to remove or rename it while some changes are made on github 
ansbile playbook2.yaml will also pull docker-image from dockerhub and create a container.
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 




#Steps_to_Setup_Project


1)First we need to launch three instances on any cloud platform for Jenkins, Ansible and Docker separetely

2)Then install java, maven and git on jenkins instance and configure it in jenkins global tool configuration

3)Install three plugin Github, Maven-Integration and publish-over-ssh

4)then create a jenkins-job as maven-project and 

 4.1)give github-repo-link and select poll-scm inside build triggers so that it should automatically update code changes made on github and 
 
 4.2)clean install inside goals and options in build section it will create a war file

5)Then integrate docker and ansible with jenkins by creating user on docker and ansible respectively using PasswordAuthentication and 
 5.1)also integrate docker with ansible using Private-Key

6)Then configure existing maven project and add post-build-action as send build artifact over ssh and executed command

 6.1)ansible-playbook /opt/docker/playbook1.yaml;
 
 6.2)sleep 10;
 
 6.3)ansible-playbook /opt/docker/playbook2.yaml


7)This will first run playbook1.yaml on the ansible-server and create docker image and tag that docker image and push it to dockerhub and 

7.1)playbook2.yaml will stop running existing container and delete container and image existing which was created earlier 

7.2)and will make new docker image and container according to changes made in soure code on github

8)after this a complete CI/CD pipeline is achieved


9)we can access our webapp by public IP of jenkins server and the port number provided for the container inside webapp section.


* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 



<img width="1440" alt="Project" src="https://user-images.githubusercontent.com/95365748/191843800-fbdc9c9a-ba7e-49ba-af3d-8aa3d4278913.png">
