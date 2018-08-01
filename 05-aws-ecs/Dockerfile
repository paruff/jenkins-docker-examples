FROM jenkins/jenkins:lts-alpine

ENV JENKINS_REF /usr/share/jenkins/ref

# RUN sudo apk update 
# RUN apk upgrade 
RUN apk add git  
RUN apk add docker

# install jenkins plugins
COPY jenkins-home/plugins.txt $JENKINS_REF/
RUN /usr/local/bin/install-plugins.sh < $JENKINS_REF/plugins.txt

ENV JAVA_OPTS -Dorg.eclipse.jetty.server.Request.maxFormContentSize=100000000 \
 			  -Dorg.apache.commons.jelly.tags.fmt.timeZone=America/Los_Angeles \
 			  -Dhudson.diyChunking=false \
 			  -Djenkins.install.runSetupWizard=false

# copy scripts and ressource files
COPY jenkins-home/*.* $JENKINS_REF/
COPY jenkins-home/userContent $JENKINS_REF/userContent
COPY jenkins-home/jobs $JENKINS_REF/jobs/
COPY jenkins-home/init.groovy.d $JENKINS_REF/init.groovy.d/
COPY jenkins-home/dsl $JENKINS_REF/dsl/
