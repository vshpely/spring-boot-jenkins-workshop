1. Build jar file
    mvn clean install
2. Create file Dockerfile
    FROM frolvlad/alpine-oraclejdk8:slim
    ADD ./target/spring-boot-jenkins-workshop-0.0.1-SNAPSHOT.jar app.jar
    RUN sh -c 'touch /app.jar'
    ENV JAVA_OPTS=""
    ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]
3. Build docker images 
    docker build .
4. Run docker container
    docker run -p 8080:8080 ID IMAGES