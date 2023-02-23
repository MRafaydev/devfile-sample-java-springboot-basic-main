FROM quay.io/devfile/maven:3.8.1-openjdk-17-slim

ENV APP_HOME=/build
WORKDIR $APP_HOME

RUN mkdir -p /tmp/cache
COPY . /tmp/cache/
RUN cp -r /tmp/cache/* $APP_HOME && rm -rf /tmp/cache/*


# Build dependency offline to streamline build
COPY pom.xml .
RUN mvn dependency:go-offline



COPY src src
RUN mvn package -Dmaven.test.skip=true 
# compute the created jar name and put it in a known location to copy to the next layer.
# If the user changes pom.xml to have a different version, or artifactId, this will find the jar 
RUN grep version /build/target/maven-archiver/pom.properties | cut -d '=' -f2 >.env-version 
RUN grep artifactId /build/target/maven-archiver/pom.properties | cut -d '=' -f2 >.env-id
RUN cp /build/target/$(cat .env-id)-$(cat .env-version).jar /build/target/export-run-artifact.jar

FROM openjdk:11-jdk
COPY --from=0 /build/target/export-run-artifact.jar  /app/target/export-run-artifact.jar

EXPOSE 8081
ENTRYPOINT [ "java", "-jar", "/app/target/export-run-artifact.jar", "--server.port=8081" ]
