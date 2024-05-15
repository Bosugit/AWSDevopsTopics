ENTRYPOINT: Specifies the command to run when the container starts.

Dockerfile:

FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]

*************************************************COMMANDS**********************************************************




build command:
    docker build -t ultimate-cicd-pipeline:v1 .

docker run:

    docker run --name container1 -d ubuntu
    kubectl run pd1 --image=nginx 

    docker run --name c3 -d -p 80:80 nginx

    docker run -d -p 8010:8080 -t ultimate-cicd-pipeline:v1

    http://<ip-address>:8010

exec:
    docker exec -it containerid bash

  kubectl exec -it pd1 bash

