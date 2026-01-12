FROM openjdk:17-jdk-slim

WORKDIR /app

COPY target/hello_render-0.0.1-SNAPSHOT.jar app.jar

# Render が自動で渡す PORT に従って起動
ENTRYPOINT ["sh", "-c", "java -jar /app/app.jar --server.port=${PORT}"]
