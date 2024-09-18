FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Natnael"
RUN apt update && apt install maven -y
RUN git clone https://github.com/ntadesse/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD CMD ["catalina.sh", "run"]
