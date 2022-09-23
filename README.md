# CI-CD-Pipeline-using-jenkins-docker-and-ansible


PROJECT_OVERVIEW
<img width="1023" alt="overview" src="https://user-images.githubusercontent.com/95365748/191949125-797f31bf-b639-47a7-b27a-2fb898f9d4bb.png">


first we need to launch three instances on any cloud platform for Jenkins, Ansible and Docker


then install java, maven and git on jenkins instance and configure it in jenkins global tool configuration


install three plugin Github, Maven-Integration and publish-over-ssh

then create a jenkins-job as maven-project and give github-repo-link and select poll-scm inside build triggers so that it should automatically update code changes made on github and clean install inside goals and options in build section it will create a war file

then integrate docker and ansible with jenkins by creating user on docker and ansible respectively using PasswordAuthentication and then also integrate docker with ansible using Private-Key

then configure existing maven project and add post-build-action as send build artifact over ssh and executed command
ansible-playbook /opt/docker/playbook1.yaml;
sleep 10;
ansible-playbook /opt/docker/playbook2.yaml


this will first run playbook1.yaml on the ansible-server and create docker image and tag that docker image and push it to dockerhub and playbook2.yaml will stop running existing container and delete container and image existing which was created earlier and will make new docker image and container according to changes made in soure code on github

after this a complete CI/CD pipeline is achieved


we can access our webapp by public IP of jenkins server and the port number provided for the container inside webapp section






<img width="1440" alt="Project" src="https://user-images.githubusercontent.com/95365748/191843800-fbdc9c9a-ba7e-49ba-af3d-8aa3d4278913.png">
