FROM jenkins/jenkins:lts-jdk11
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/ref/jenkins.yaml
COPY files/jenkins.yaml /usr/share/jenkins/ref/jenkins.yaml
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
USER root
RUN apt-get update && \
    apt-get install -y python3-pip git binutils && \
    pip3 install botocore && \
    apt-get clean
RUN git clone https://github.com/aws/efs-utils && \
    cd efs-utils && \
    ./build-deb.sh && \
    apt-get install -y ./build/amazon-efs-utils*deb
USER jenkins
COPY files/InitialConfig.groovy /usr/share/jenkins/ref/init.groovy.d/InitialConfig.groovy
COPY files/plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt
