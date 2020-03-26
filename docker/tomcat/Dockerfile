FROM alpine:3.4

MAINTAINER isystk

ENV TOMCAT_MAJOR=8 \
    TOMCAT_VERSION=8.5.53 \
    TOMCAT_HOME=/opt/tomcat \
    CATALINA_HOME=/opt/tomcat \
    CATALINA_OUT=/dev/null

RUN mkdir -p /opt && \
    apk upgrade --update && \
    apk add --update openjdk8-jre curl && \
    curl -jksSL -o /tmp/apache-tomcat.tar.gz http://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR}/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    tar -C /opt -xvzf /tmp/apache-tomcat.tar.gz && \
    ln -s /opt/apache-tomcat-${TOMCAT_VERSION} ${TOMCAT_HOME} && \
    rm -rf ${TOMCAT_HOME}/webapps/* && \
    apk del curl && \
    rm -rf /tmp/* /var/cache/apk/*

EXPOSE 8080
ENTRYPOINT [ "/opt/tomcat/bin/catalina.sh", "run" ]
