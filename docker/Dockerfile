# Use a modern JDK 11 base image
FROM eclipse-temurin:11-jdk:alpine


EXPOSE 8070

# App directory
ENV APP_HOME /usr/src/app
WORKDIR $APP_HOME

# Copy built jar
COPY target/shopping-cart-0.0.1-SNAPSHOT.jar app.jar


ENV JAVA_OPTS="-Xms128m -Xmx512m -Djava.security.egd=file:/dev/./urandom -Djava.io.tmpdir=/tmp"

# ENTRYPOINT wrapped in sh -c for Alpine stability
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar app.jar"]
