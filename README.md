# DevOps Project for beginer

- In this project I will tech how to set up a CI/CD pipeline with Jenkins, Sonarqude and Docker. For that we need aws account with three EC2 instance one for Sonarqube, one for Jenkins and one for Docker.

## Diagram

![DevOps Project-1](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/8310c2e8-73f4-4eff-b8ec-f53c0d65eacd)

## Steps

1. Push code to the github repository and allow webhook from repository seetings.
2. Launch three EC2 instance with Linux or any other OS.
3. Install Jenkins in one of the EC2 server.
4. Install Sonarqube in second EC2 server.
5. Install Docker in last EC2 server.
6. Pull code form github to jenkins server.
7. Send code to Sonarqube server for Analysis.
8. After passing analysis stage deploy code to docker server.
9. Access docker server for the hosting purpose of application.

## Install Jenkins on EC2 server

Link: https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

1. Code:


    - sudo yum update –y
    - sudo wget -O /etc/yum.repos.d/jenkins.repo \https://pkg.jenkins.io/redhat-stable/jenkins.repo
    - sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
    - sudo yum upgrade
    - sudo amazon-linux-extras install java-openjdk11 -y
    - sudo dnf install java-11-amazon-corretto -y
    - sudo yum install jenkins -y
    - sudo systemctl enable jenkins
    - sudo systemctl start jenkins
    - sudo systemctl status jenkins


* Now after installation go to http://public_ip_jenkins_server:8080 and you will see below image.

<br>

![jenkins-1](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/674da5c2-654e-4e33-90b8-e85730fbbdba)

2. Go the path which is in red highlighted and get the password and write it over here.

<br>

![image](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/a0dae4c9-c9d0-44c9-bca5-78f5fb3b1728)

3. Create user with password.

<br>

![image](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/66a331a5-8d3b-4aa7-ad4b-344e091d5f7e)

4. Now create a Freestyle project.

![image](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/865c570d-084e-4074-af64-da90d2708c65)

5. Add github repo over here as a source code.

![image](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/effcd074-941d-4a3a-bcc6-d3d961e7891d)

6. Check the github hook triger.

## Install sonarqube

Link: https://www.sonarsource.com/products/sonarqube/downloads/

1. Download sonarqube community version in linux through wget command.
2. Unzip the folder.
3. Navigate to the linux folder and run bash file over there. 
4. Install java 17 version for sonarqube.
5. After installation process go to browser and go to the http://public_ip_sonarqube_server:9000
6. Default login is admin admin and then change the paswword.
7. Navigate to the Manual process.
8. Give project name and project key.
9. Select with Jenkins and then github.
10. Skip all the steps and hit continue do not change any configuration.
11. Select application technology.
12. Copy project key for future use.
13. Click finish and go to the security under admin and generate token for global jenkins project. And save that token for future use.
14. Go to Jenkins server to install sonarqube plugins.
15. Go to manage Jenkins and then available plugins and install sonaqube scanner.
16. After installation go to global configuration and add sonarqube project and add in the configure tab add project key and soanrqube address.


## Install Docker host

Link: https://docs.docker.com/engine/install/ubuntu/

1. After installation go to jenkins dashboard and then server group center where add docker server.

![image](https://github.com/harsh-viradia/DevOps-Project-1/assets/140060556/7c950149-9778-4d87-a08d-2208c6912a89)

2. After then add docker file in the docker server and build image for webserver and copy all files from github repo to docker server and host it.

This is how Jenkins CI/CD pipline works.
