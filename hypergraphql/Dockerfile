FROM openjdk:8-jdk-alpine
WORKDIR /
ADD https://www.hypergraphql.org/resources/hypergraphql-1.0.3-exe.jar /hypergraphql.jar
ADD ./config config
EXPOSE 8081
ENV JAVA_OPTS=''
ENTRYPOINT ["java", "-jar", "/hypergraphql.jar", "-config", "config"]