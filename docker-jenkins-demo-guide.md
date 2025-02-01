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


![docker-version-cmdline-screenshot](https://github.com/user-attachments/assets/3eb59ce0-8d18-4e03-a2f2-225fbe19d154)


(2) Search for the official Jenkins container image on Docker Hub using either Docker Desktop application
or docker command line.

![docker-desktop-jenkins-search](https://github.com/user-attachments/assets/61d84d21-9404-4fbb-b778-07aa04a273d6)


// Docker Command Line Example.

Note: You will see a long list of jenkins images but you will use the one named jenkins/jenkins or 
jenkins/jenkins:lts. The "lts" is the long term support version.

$ docker search jenkins


![docker-cmdline-jenkins-search](https://github.com/user-attachments/assets/890e2859-7742-4a54-9508-f0c39bb0dc76)


In docker desktop select pull and the image will be downloaded to your information system. Once downloaded you should see it listed in the Docker Desktop application images innventory. 

Note: you can do the same from the command line:


![docker-pull-jenkins](https://github.com/user-attachments/assets/da463bba-7294-46e0-986c-4b949f69fa37)

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

![docker-run-jenkins](https://github.com/user-attachments/assets/07dfde4f-1505-4e7d-bb4a-c19a07ca21d3)

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





