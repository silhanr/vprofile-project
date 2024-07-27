FROM openjdk:11 As BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone --branch docker https://github.com/silhanr/vprofile-project.git 
RUN cd vprofile-project && mvn install


FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
LABEL "Project"="Vprofile"
LABEL "Author"="Roman"

EXPOSE 8080
CMD ["catalina.sh", "run"]
