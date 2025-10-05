# Etapa 1: Build do Gradle
FROM gradle:8.14.3-jdk17 AS builder
WORKDIR /app

# Copia apenas o conteúdo da pasta backend
COPY backend/ .

# Roda o build e gera o JAR
RUN gradle build --no-daemon

# Etapa 2: Criar a imagem final com apenas o JAR
FROM openjdk:17-jdk-slim
WORKDIR /app

# Copia o JAR gerado da etapa de build
COPY --from=builder /app/build/libs/*.jar app.jar

# Expõe a porta do Spring Boot (ajuste se necessário)
EXPOSE 8080

# Comando para rodar o Spring Boot
ENTRYPOINT ["java", "-jar", "app.jar"]
