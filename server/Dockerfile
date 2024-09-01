FROM maven:3.8.5-openjdk-17 as build

WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Use a imagem base do OpenJDK 17
FROM openjdk:17

# Define uma variável de ambiente para o diretório de trabalho
ENV APP_DIR /app

# Define o diretório de trabalho dentro do container
WORKDIR $APP_DIR

COPY --from=build ./app/target/*.jar ./app.jar

EXPOSE 8081

CMD ["java", "-jar", "app.jar"]
