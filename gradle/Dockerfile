FROM ubuntu:16.04
MAINTAINER Hari Sekhon (https://www.linkedin.com/in/harisekhon)

LABEL Description="Java + Ubuntu (OpenJDK)"

ENV DEBIAN_FRONTEND noninteractive

ARG JAVA_VERSION=9
ARG JAVA_RELEASE=JDK

ENV JAVA_HOME=/usr

RUN bash -c ' \
set -euxo pipefail && \
apt-get update && \
pkg="openjdk-$JAVA_VERSION"; \
if [ "$JAVA_RELEASE" = "JDK" ]; then \
pkg="$pkg-jdk-headless"; \
else \
pkg="$pkg-jre-headless"; \
fi; \
apt-get install -y --no-install-recommends wget unzip "$pkg" && \
apt-get clean'


CMD /bin/bash

#install Gradle
RUN wget -q https://services.gradle.org/distributions/gradle-4.5.1-bin.zip \
&& unzip gradle-4.5.1-bin.zip -d /opt \
&& rm gradle-4.5.1-bin.zip

# Set Gradle in the environment variables
ENV GRADLE_HOME /opt/gradle-4.5.1
ENV PATH $PATH:/opt/gradle-4.5.1/bin
