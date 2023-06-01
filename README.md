# observability


#install docker and docker-compose

sudo yum update

sudo yum install docker -y

sudo usermod -a -G docker ec2-user

newgrp docker

wget https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) 

sudo mv docker-compose-$(uname -s)-$(uname -m) /usr/local/bin/docker-compose

sudo chmod -v +x /usr/local/bin/docker-compose

sudo systemctl enable docker.service

sudo systemctl start docker.service



#install git
sudo yum install git -y



#install 
git clone -b main https://github.com/ruizivo/observability.git && cd observability && docker-compose up -d



# adicionar o javaagent


usando o arquivo de propriedade
-javaagent:/opt/observability/opentelemetry-javaagent.jar -Dotel.service.name=nomeProjeto -Dotel.javaagent.configuration-file=/opt/observability/observability.properties

passando cada variável
-javaagent:/opt/observability/opentelemetry-javaagent.jar -Dotel.service.name=nomeProjeto -Dotel.exporter.otlp.endpoint=http://observability.hivecloud.com.br:14317 -Dotel.logs.exporter=otlp -Dotel.traces.exporter=otlp -Dotel.metrics.exporter=otlp -Dotel.metric.export.interval=10000 -Dotel.integration.jdbc.datasource.enabled=true -Dotel.instrumentation.jdbc.datasource.enabled=true -Dotel.instrumentation.common.db-statement-sanitizer.enabled=false