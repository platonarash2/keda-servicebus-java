FROM maven:3.8-adoptopenjdk-16 as build

WORKDIR /app

COPY pom.xml .
COPY src src

RUN mvn clean package

#RUN ls -la .
#RUN ls -la ./target

FROM openjdk:16-alpine




COPY --from=build \
    /app/target/* \
    /app/target/

RUN ls /app/target
#COPY --from=build \
#    /app/target/KedaJavaServiceBus-1.0.0.jar \
#    /app/target/KedaJavaServiceBus-1.0.0.jar

ENTRYPOINT ["java", "-jar", "/app/target/KedaJavaServiceBus-1.0.0.jar"]