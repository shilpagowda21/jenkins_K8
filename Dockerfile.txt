FROM openjdk:8-alpine

# Required for starting application up.
RUN apk update && apk add /bin/sh

RUN mkdir -p /opt/app
ENV PROJECT_HOME /opt/app

COPY target/demo 0.0.1-SNAPSHOT.war $PROJECT_HOME/helloworld.war

WORKDIR $PROJECT_HOME
EXPOSE 8080
CMD ["java" ,"-war","./helloworld.war"]