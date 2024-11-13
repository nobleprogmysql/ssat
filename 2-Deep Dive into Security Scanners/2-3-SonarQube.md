## install docker
sudo snap install docker

## run SonarQube image in Docker using commands:
sudo docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:latest

## run sonar scanner docker image
docker run --rm sonarsource/sonar-scanner-cli -v /home/student/sonar-qube/bruno-main:/project



## download and install sonar-scanner 
https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-6.2.1.4610-linux-x64.zip
unzip sonar-scanner-cli-6.2.1.4610-linux-x64.zip

sudo mv  sonar-scanner-6.2.1.4610-linux-x64/ /opt/sonar-scanner

nano ~/.bashrc
export SONAR_SCANNER_HOME=/opt/sonar-scanner
export PATH=$PATH:$SONAR_SCANNER_HOME/bin
ctr+x Y enter to save

source ~/.bashrc


cd /home/student/sonar-qube/bruno-main/

sonar-scanner   -Dsonar.projectKey=demoproject   -Dsonar.sources=.   -Dsonar.host.url=http://localhost:9000   -Dsonar.token=sqp_bbe702b946c2504fc5834dae9cb2ac0519674448

## sonar documentation
https://docs.sonarsource.com/sonarqube/latest/try-out-sonarqube/