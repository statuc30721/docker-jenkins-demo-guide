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
- Create a container running on the information system
- Map the computer that docker is running on to ports 8080 and 50000.
- Create a folder named <jenkins_home> and map it to the containers folder </var/jenkins_home>.
- Use the source image named jenkins:lts-jdk11.

// Docker run example

![docker-run-jenkins](https://github.com/user-attachments/assets/07dfde4f-1505-4e7d-bb4a-c19a07ca21d3)

(5) Locate the password created during the Jenkins container's initial startup.


Note: The password location will be in /var/jenkins_home/secrets/InitialAdminPassword

(6) Access jenkins via a web browser at the following URL: http://localhost:8080.
Note: You will need the password you should have seen in the command line to login
the jenkins web portal.

![initial-unlock-jenkins-screenshot](https://github.com/user-attachments/assets/afb08314-e8f1-4bf6-b1fe-e8b688a4942a)


(7) Select the recommended Jenkins plugins. This can take some time to finish.

![jenkins-customize-screenshot](https://github.com/user-attachments/assets/d17bbc29-2022-4e3d-b713-b83cf0b29c38)


![jenkins-initial-plugins](https://github.com/user-attachments/assets/31fd276f-bfb0-4bc7-ab28-720f70cae54e)


(8) Create a new user account. Document the username and password you created during this step.

![jenkins-create-first-admin-user](https://github.com/user-attachments/assets/a949b4f5-5d37-488f-91a3-e1cbea3998e8)


(9) Set URL that you want jenkins to listen on. In this example that is http://localhost:8080.

![jenkins-set-url](https://github.com/user-attachments/assets/e1adb806-7c38-4dac-b93f-c3af8a7e868e)


(10) If successful you should see the message "Jenkins is ready!" Select the "start using jenkins" button.

![jenkins-is-ready](https://github.com/user-attachments/assets/8e4807e9-8bf5-40d3-9773-08402c6dbe5e)


(11) You should see a page stating "Wecome to Jenkins!".


![welcome-to-jenkins](https://github.com/user-attachments/assets/27101ff9-b504-43bd-8bbb-b5bdd9cd11cc)





