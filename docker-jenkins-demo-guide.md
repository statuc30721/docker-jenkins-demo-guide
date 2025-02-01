# Build a Jenkins container leveraging Docker.

Pre-requisites:
- Docker and Docker-compose installed via commandline using your operating system package installation software (e.g. Homebrew https://brew.sh/ for MacOS/Linux or Chocolately https://chocolatey.org/ for Windows )

- Docker Desktop https://www.docker.com/products/docker-desktop/ to provided a graphical user interface. This is especially a good application to use if you are new to containers and Docker. 

- A docker account to interact with docker services like Docker Hub, https://app.docker.com/login.

Note: To get familiar with Docker and running containers on docker
Reference: https://www.docker.com/get-started/

(1) Create an account on Docker Hub.
https://hub.docker.com/

![docker-hub-screenshot](https://github.com/user-attachments/assets/bfdb0500-fa69-4f93-ab3d-41b23130a2e0)

Once you have created an account on Docker Hub. Download the docker desktop application for your operating system.

Installing Docker desktop will include docker-compose as well. You will use Docker Hub to upload and download container
images you create over time as you work with docker and containers.

- Verify docker desktop is installed. 
After installing the docker desktop application, start the docker desktop application and login to your docker hub account
using the docker application.

![docker-desktop-application-screenshot](https://github.com/user-attachments/assets/d418c07a-a4cc-4464-bc1c-80700ce1b78b)


- Verify docker command line works.
Note: This is being run on MacOS. You should see similar output on a Linux or Windows based operating system.

$ docker version




(2) Search for the official Jenkins container image on Docker Hub using either Docker Desktop application
or docker command line.

![docker-desktop-jenkins-search](https://github.com/user-attachments/assets/61d84d21-9404-4fbb-b778-07aa04a273d6)


// Docker Command Line Example.

Note: You will see a long list of jenkins images but you will use the one named jenkins/jenkins or 
jenkins/jenkins:lts. The "lts" is the long term support version.

$ docker search jenkins
NAME                               DESCRIPTION                                     STARS     OFFICIAL
jenkins/jenkins                    The leading open source automation server       4085      
jenkins                            DEPRECATED; use "jenkins/jenkins:lts" instead   5696      [OK]
jenkins/jnlp-agent-maven           A JNLP-based agent with Maven 3 built in        10        
jenkins/ssh-agent                  Docker image for Jenkins agents connected ov…   60        
jenkins/inbound-agent              This is an image for Jenkins agents using TC…   140 

In docker desktop select pull and the image will be downloaded to your information system. Once downloaded you should see it listed in the Docker Desktop application images innventory. 

Note: you can do the same from the command line:

$ docker pull jenkins/jenkins
Using default tag: latest
latest: Pulling from jenkins/jenkins
fa8785a0cbfc: Download complete 
70ae892edd2c: Download complete 
e228c44fff3b: Download complete 
e474a4a4cbbf: Download complete 
40375a76d092: Download complete 
154b66b7ce12: Download complete 
eeeada77dafa: Download complete 
764eeac48f0c: Download complete 
25617dd6d7e8: Download complete 
03bb4613691f: Download complete 
793748ac1b11: Download complete 
8c3f2fecd07d: Download complete 
Digest: sha256:119e9decb712ec14aace4343ac4203ef2ba4d6cb7dbcb5387c76b85b29dd15fd
Status: Downloaded newer image for jenkins/jenkins:latest
docker.io/jenkins/jenkins:latest

(3) Log into the Docker Hub via the command line. You should see a similar result below.
You can use either GitBash (on windows) or the terminal (on MacOS or Linux).

// Docker login via command line example.

$ docker login
Authenticating with existing credentials...
Login Succeeded

(4) Once you have successfully logged into docker, run the following command:
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11

Note: 
This is telling docker to perform the following tasks (in no particluar order):
a. Create a container running on the information system
b. Map the computer that docker is running on to ports 8080 and 50000.
c. Create a folder named <jenkins_home> and map it to the containers folder </var/jenkins_home>.
d. Use the source image named jenkins:lts-jdk11.

// Docker run example

$ docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
Unable to find image 'jenkins/jenkins:lts-jdk11' locally
lts-jdk11: Pulling from jenkins/jenkins
8bbe33c1a45d: Download complete 
f62c370bc989: Download complete 
75d89130f4e0: Download complete 
4760cf60c6e6: Download complete 
6a4c33872faf: Download complete 
5e0034fcdff5: Download complete 
39252305a35d: Download complete 
ec694b08d3fc: Download complete 
6d11c181ebb3: Download complete 
4a9739527a50: Download complete 
a9af1892fb19: Download complete 
1b4ed656dd0a: Download complete 
Digest: sha256:6aa6c6bd7da914bf5333305c8102cb26965ea4b227e37f4269315725a2b0cd81
Status: Downloaded newer image for jenkins/jenkins:lts-jdk11
Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war

(5) Locate the password created during the Jenkins container's initial startup.


Note: The password location will be in /var/jenkins_home/secrets/InitialAdminPassword

(6) Access jenkins via a web browser at the following URL: http://localhost:8080.
Note: You will need the password you should have seen in the command line to login
the jenkins web portal.

(7) Select the recommended Jenkins plugins. This can take some time to finish.

(8) Create a new user account. Document the username and password you created during this step.

(9) Set URL that you want jenkins to listen on. In this example that is http://localhost:8080.

(10) If successful you should see the message "Jenkins is ready!"

(11) Select the button <start using jenkins>.

(12) You should see a page stating "Wecome to Jenkins!".





