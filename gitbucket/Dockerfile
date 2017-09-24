FROM tomcat:8.5-jre8-alpine

LABEL maintainer "Hidetoshi Imai <hidepin@gmail.com>"

RUN rm -rf $CATALINA_HOME/webapps/*
ADD https://github.com/gitbucket/gitbucket/releases/download/4.16.0/gitbucket.war $CATALINA_HOME/webapps/gitbucket.war
RUN ln -s /opt/gitbucket /root/.gitbucket

VOLUME /opt/gitbucket

# Port for web page
EXPOSE 8080
# Port for SSH access to git repository (Optional)
EXPOSE 29418

CMD ["catalina.sh", "run"]
