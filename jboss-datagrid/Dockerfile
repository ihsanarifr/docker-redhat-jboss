# Use latest jboss/base-jdk:8 image as the base
FROM jboss/base-jdk:8

MAINTAINER Ihsan Arif Rahman <ihsanarif@gmail.com>

# Set the JBOSS_VERSION env variable
ENV JBOSS_VERSION 7.1
ENV JBOSS_HOME /opt/jboss/jboss-datagrid

USER root

COPY source/jboss-datagrid-$JBOSS_VERSION.zip $HOME

# Add the JBoss distribution to /opt, and make jboss the owner of the extracted zip content
# Make sure the distribution is available from a well-known place
RUN cd $HOME
RUN unzip jboss-datagrid-$JBOSS_VERSION.zip
RUN mv jboss-datagrid-$JBOSS_VERSION $JBOSS_HOME \
    && rm jboss-datagrid-$JBOSS_VERSION.zip \
    && chown -R jboss:0 ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME}

# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

USER jboss

# Add a user in administration realm
RUN $JBOSS_HOME/bin/add-user.sh admin Admin#007 --silent

# Expose the ports we're interested in
EXPOSE 8080 9990

# Set the default command to run on boot
# This will boot JBoss EAP in the standalone mode and bind to all interface
CMD ["/opt/jboss/jboss-datagrid/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]