Installing SonarQube on Ubuntu EC2 Instance

We’ll be installing SonarQube inside docker and will use docker-compose to spin up the SonarQube Instance inside our ubuntu instance.

Paste the below commands in your ubuntu instance after connecting with it

# Install docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
apt-cache policy docker-ce
sudo apt-get install -y docker-ce
sudo usermod -aG docker ubuntu
sudo systemctl status docker
#Press CTRL+C or CTRL+Z to exit from the above command
#Install docker compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
#Change permissions
sudo chmod +x /usr/local/bin/docker-compose
#Check the version
docker-compose --version
#Install sonar
sudo sysctl -w vm.max_map_count=262144
mkdir sonar
wget https://raw.githubusercontent.com/awstechguide/devops/master/docker-compose.yml
sudo su
cd sonar
docker–compose up
Once all the above commands are executed, SonarQube will be successfully installed and will be running.

SonarQube runs on Port 9000, so in order to connect to the SonarQube Dashboard, we can use the public IP address of the Ubuntu instance with port 9000 at the end.

Go to AWS EC2 Console, select the Ubuntu EC2 you’ve created, and check for the public IP address below


You can connect with the SonarQube dashboard at http://13.232.164.32:9000/

The default credentials for the SonarQube will be as below

Username:admin

Password: admin

With the above credentials, log in to the SonarQube Dashboard, and let’s start the actual work(after changing the default password). You’ll see the below screen after logging in.


https://awstip.com/installing-sonarqube-on-aws-ec2-instance-and-integrating-it-with-aws-codepipeline-abec99416ba4
