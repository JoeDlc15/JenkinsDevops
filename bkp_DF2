FROM jenkins/jenkins:lts

USER root

# Instalar docker-cli y utilidades
RUN apt-get update && \
    apt-get install -y docker.io zip unzip && \
    apt-get clean

# Permitir a Jenkins usar docker (muy importante)
RUN groupadd -f docker
RUN usermod -aG docker jenkins

USER jenkins