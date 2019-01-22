# Use latest jboss/base-jdk:8 image as the base
FROM jboss/base-jdk:8

MAINTAINER Ihsan Arif Rahman <ihsanarif@gmail.com>

# Set the JBOSS_VERSION env variable
ENV JBOSS_VERSION 7.0.1
ENV JBOSS_HOME /opt/jboss/jboss-fuse

# # Install maven
# ARG MAVEN_VERSION=3.5.4
# ARG USER_HOME_DIR="/root"
# ARG SHA=ce50b1c91364cb77efe3776f756a6d92b76d9038b0a0782f7d53acf1e997a14d
# ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries



USER root

COPY source/jboss-fuse-$JBOSS_VERSION.zip $HOME

# Add the JBoss distribution to /opt, and make jboss the owner of the extracted zip content
# Make sure the distribution is available from a well-known place
RUN cd $HOME
RUN unzip jboss-fuse-$JBOSS_VERSION.zip
RUN mv jboss-fuse-$JBOSS_VERSION $JBOSS_HOME \
    && rm jboss-fuse-$JBOSS_VERSION.zip \
    && chown -R jboss:0 ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME} \
    && rm -rf $JBOSS_HOME/quickstarts \
    && rm -rf $JBOSS_HOME/extras

COPY etc/users.properties $JBOSS_HOME/etc/

# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

USER jboss

# Expose the ports we're interested in
EXPOSE 8181 8101 1099 44444 61616

# Set the default command to run on boot
CMD $JBOSS_HOME/bin/fuse server

# After run install feature
CMD cd $JBOSS_HOME/bin && \
    ./client -a 8101 -h localhost -u admin -p admin features:install camel-sql camel-gson camel-servlet camel-http camel-http4 camel-jetty camel-jsonpath camel-cxf camel-activemq activemq-client camel-infinispan