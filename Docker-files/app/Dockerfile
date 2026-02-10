FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
RUN git clone https://github.com/EnzoT454/Docker-containerization.git
RUN cd Docker-containerization && git checkout main && mvn install

FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Imran"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Docker-containerization/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
