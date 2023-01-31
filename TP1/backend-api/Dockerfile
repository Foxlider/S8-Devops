# FROM eclipse-temurin:17-alpine
# COPY ./src /usr/src/myapp
# WORKDIR /usr/src/myapp
# RUN javac Main.java
# CMD ["java", "Main"]

# FROM eclipse-temurin:17-jre-alpine
# # Build Main.java
# # TODO : in next steps (not now)
# COPY --from=0 /usr/src/Main.class .

# Build
FROM maven:3.8.7-eclipse-temurin-17-alpine AS myapp-build
ENV MYAPP_HOME /opt/myapp
WORKDIR $MYAPP_HOME
COPY src/pom.xml .
COPY src/src ./src
RUN mvn dependency:go-offline
RUN mvn package -DskipTests

# Run
FROM eclipse-temurin:17-alpine
ENV MYAPP_HOME /opt/myapp
WORKDIR $MYAPP_HOME
COPY --from=myapp-build $MYAPP_HOME/target/*.jar $MYAPP_HOME/myapp.jar

ENTRYPOINT java -jar myapp.jar