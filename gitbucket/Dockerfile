FROM tomcat:8.5-jre8-alpine

LABEL maintainer "Hidetoshi Imai <hidepin@gmail.com>"

ARG GITBUCKET_VERSION
ENV GITBUCKET_VERSION ${GITBUCKET_VERSION:-4.23.0}
ARG MAVEN_VERSION
ENV MAVEN_VERSION ${MAVEN_VERSION:-3.5.2}

RUN rm -rf $CATALINA_HOME/webapps/*
ADD https://github.com/gitbucket/gitbucket/releases/download/${GITBUCKET_VERSION}/gitbucket.war $CATALINA_HOME/webapps/gitbucket.war
RUN ln -s /opt/gitbucket /root/.gitbucket

RUN apk add --no-cache openjdk8
RUN mkdir -p /opt && cd /opt && wget -O - http://ftp.tsukuba.wide.ad.jp/software/apache/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz | tar zxf -
ENV PATH $PATH:/opt/apache-maven-${MAVEN_VERSION}/bin

VOLUME /opt/gitbucket
VOLUME /root/.m2

# Port for web page
EXPOSE 8080
# Port for SSH access to git repository (Optional)
EXPOSE 29418

CMD ["catalina.sh", "run"]
