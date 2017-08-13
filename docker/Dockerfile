#
# Centos python base
#

# Pull base image.
FROM centos:7.3.1611
MAINTAINER Nicolas Fraison <nfraison@yahoo.fr>

ENV MAVEN_VERSION=3.3.9
ENV JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk
ENV PATH=/apps/maven/bin:$PATH

# Deploy epel and python
RUN yum install -y epel-release
RUN yum install -y java-1.8.0-openjdk-devel \
                   git \
                   protobuf \
                   protobuf-compiler \
                   bzip2 && \
    yum clean all

# Deploy Maven
RUN mkdir -p /apps/maven && \
    curl -L -s -S \
         http://mirrors.ircam.fr/pub/apache/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
         -o /apps/maven.tar.gz && \
    tar xzf /apps/maven.tar.gz --strip-components 1 -C /apps/maven && \
    rm -f /apps/maven.tar.gz

# Define default command.
CMD /bin/bash
