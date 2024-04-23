ENTRYPOINT: Specifies the command to run when the container starts.

Dockerfile:

FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]


build command:
docker build -t ultimate-cicd-pipeline:v1 .

run:
docker run -d -p 8010:8080 -t ultimate-cicd-pipeline:v1

http://<ip-address>:8010

