# 安定版の OpenJDK 17 イメージ
FROM eclipse-temurin:17-jdk-focal

# 作業ディレクトリ
WORKDIR /app

# Mavenでビルドしたjarをコピー
COPY target/hello_render-0.0.1-SNAPSHOT.jar app.jar

# Render の PORT 環境変数を設定
ENV PORT $PORT

# 起動コマンド
ENTRYPOINT ["java","-jar","/app/app.jar"]
