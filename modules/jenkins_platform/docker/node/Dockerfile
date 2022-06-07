FROM docker.io/jenkins/inbound-agent:4.10-3

USER root

RUN apt-get update && \
    apt-get install -y wget unzip && \
    wget  https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip && \
    unzip awscli-exe-linux-x86_64.zip && \
    ./aws/install && \
    wget https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip && \
    unzip aws-sam-cli-linux-x86_64.zip -d sam-installation && \
    ./sam-installation/install && \
    rm -rf aws* sam*

RUN aws --version && \
    sam --version
