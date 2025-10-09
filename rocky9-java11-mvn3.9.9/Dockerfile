FROM rockylinux:9


RUN useradd jenkins

ARG MAVEN_VERSION=3.9.9

RUN yum update -y && \
  yum install -y which && \
  yum clean all

RUN yum install -y java-17-openjdk-devel

# Maven
RUN curl -fsSL https://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
  && mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_VERSION=${MAVEN_VERSION}
ENV M2_HOME /usr/share/maven
ENV maven.home $M2_HOME
ENV M2 $M2_HOME/bin
ENV PATH $M2:$PATH
ENV TESTCONTAINERS_RYUK_DISABLED=true
