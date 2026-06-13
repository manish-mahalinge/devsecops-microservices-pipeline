Install Docker And DOcker compose And Jenkins 
================================
start-sonarqube
--
docker run -itd --name sonarqube-server -p 9000:9000 sonarqube:lts-community
-----------------------------
install trivy
sudo apt-get update
sudo apt-get install -y wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | \
gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | \
sudo tee /etc/apt/sources.list.d/trivy.list

sudo apt-get update
sudo apt-get install -y trivy
</details>
-----------------------------------------------------------------------------------------------

GO To Jenkins And Install Plugins 
---------
1)OWASP
2)SOnarqube Scanner
3)Docker
4)Sonar Quality Gates
--------------------------------------------

Go to sonarqube Create webhook
--
Name-any name 
URL-http://13.234.76.179:8080/sonarqube-webhook/ 
then 
GO to security -user
and create TOKEN from existing user
===========================
setup sonarqube in jenkins
Go to Jenkins manage Jenkins -> System

1)sonarqube server -add

Name
Sonar
Server URL
Default is http://localhost:9000
http://13.234.76.179:9000
Server authentication token
SonarQube authentication token. Mandatory when anonymous access is disabled.

add credentials 
--
Add Secret text
Secret
••••••••••••••••••••••••••••••••••••••••••••
ID
Sonar
Description
Sonar
=======================
Install SOnarquality gates
GO to manage Jenkins TOols 
-Install Sonarscanner
Name
Sonar

Version
SonarQube Scanner 5.0.1.3006

 2) Install OWASP TOOL
- Dependency CHeck
- Name -dc
  Install Automactic tick
  Github.com - version 9.1.0
  ====================

  Make Declarative pipeline
  select pipeline option
  -Give namee
  -
  ################################################

  Error fixing fast
  -ADd jenkins to Docker Group
  -check docker compose version is same as jenkinsfile
  ====
  commands
  --------


  sudo usermod -aG docker jenkins
sudo systemctl restart docker
sudo systemctl restart jenkins
sudo chmod 666 /var/run/docker.sock

