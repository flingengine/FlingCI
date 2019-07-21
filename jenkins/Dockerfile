FROM jenkins/jenkins
LABEL maintainer="benjamin.hoffman.dev@gmail.com"

# Create log folder
USER root
RUN mkdir /var/log/jenkins

RUN apt-get update

# Copy plugin settings
COPY plugins.txt /var/jenkins_home/plugins.txt
RUN /usr/local/bin/plugins.sh /var/jenkins_home/plugins.txt

# Add jobs
COPY jobs/1-fling-engine-job.xml /usr/share/jenkins/ref/jobs/1-fling-engine-job/config.xml

# Make a log directory and a jenkins user
RUN chown -R jenkins:jenkins /var/log/jenkins
USER jenkins

# Setting up environment variables for Jenkins admin user
ENV JENKINS_USER admin
ENV JENKINS_PASS admin

# Set default options
ENV JAVA_OPTS="-Xmx4096m -Djenkins.install.runSetupWizard=false"
ENV JENKINS_OPTS=" --handlerCountMax=100"