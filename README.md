# CI-CD-Pipeline-using-jenkins-docker-and-ansible

first we need to launch three instances on any cloud platform for Jenkins, Ansible and Docker.
then install java, maven and git on jenkins instance and configure it in jenkins global tool configuration
install three plugin Github, Maven-Integration and publish-over-ssh

then create a jenkins-job as maven-project and give github-repo-link and clean install inside goals and options in build section it will create a war file

then integrate docker and ansible with jenkins by creating user on docker and ansible respectively using PasswordAuthentication and then also integrated docker with ansible using Private-Key

then configure existing maven project and add post-build-action as send build artifact over ssh and executed command
ansible-playbook /opt/docker/playbook1.yaml;
sleep 10;
ansible-playbook /opt/docker/playbook2.yaml
this will create a CI/CD Pipeline 



<img width="1440" alt="Project" src="https://user-images.githubusercontent.com/95365748/191843800-fbdc9c9a-ba7e-49ba-af3d-8aa3d4278913.png">
