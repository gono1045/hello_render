# ------------------------------
# Build stage: Maven で jar を作成
# ------------------------------
FROM maven:3.9.2-eclipse-temurin-17 AS build

# 作業ディレクトリ
WORKDIR /app

# 依存関係を先にコピーしてキャッシュ活用
COPY pom.xml .
RUN mvn dependency:go-offline -B

# ソースコードをコピー
COPY src ./src

# Jar をビルド（テストはスキップ）
RUN mvn clean package -DskipTests

# ------------------------------
# Run stage: 実行用イメージ
# ------------------------------
FROM eclipse-temurin:17-jdk-focal

# 作業ディレクトリ
WORKDIR /app

# Build stage から jar をコピー
COPY --from=build /app/target/hello_render-0.0.1-SNAPSHOT.jar app.jar

# Render の PORT 環境変数を Spring Boot に設定
ENV PORT $PORT

# 起動コマンド
ENTRYPOINT ["java","-jar","/app/app.jar"]
