# Observability

Install docker and docker-compose
 
 	sudo yum update
	sudo yum install docker -y
	sudo usermod -a -G docker ec2-user
	newgrp docker
	wget https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)
	sudo mv docker-compose-$(uname -s)-$(uname -m) /usr/local/bin/docker-compose
	sudo chmod -v +x /usr/local/bin/docker-compose
	sudo systemctl enable docker.service
	sudo systemctl start docker.service

Install git

    sudo yum install git -y

install

    git clone -b main https://github.com/ruizivo/observability.git


# Adicionar o javaagent

    -javaagent:/opt/observability/opentelemetry-javaagent.jar -Dotel.service.name=accounts -Dotel.javaagent.configuration-file=/opt/observability/observability.properties
