# pipedock
Testing jenkins pipelines in combination with docker

Requirements :

One linux machine (instructions assume centos 7, execute with root priviledges)
- Add docker-ce 
	- yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
	- yum install docker-ce
    - Don't forget to add your user to the docker group to allow that user access to docker: usermod -aG docker <userid>
- Add jenkins
	Although I would have preferred to use a containerized jenkins, 
	access to docker on the host is needed for jenkins, so for now
	I have used the rpm distribution
	- yum-config-manager --add-repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
	- rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
	- yum install java jenkins
	- systemctl enable jenkins
	- systemctl start jenkins
	- NOTE: config file will be /etc/sysconfig/jenkins
	- NOTE: more info on https://wiki.jenkins.io/display/JENKINS/Installing+Jenkins+on+Red+Hat+distributions
	- add docker plugins to jenkins (docker plugin / docker API plugin)
	- usermod -a -G docker jenkins
	- systemctl restart jenkins
- Create a new job in jenkins:
	- multibranch pipeline
	- git url : https://github.com/madm1c/pipedock.git
