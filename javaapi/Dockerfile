FROM eclipse-temurin:8 AS build_image
WORKDIR /usr/app
COPY ./ /usr/app/
RUN apt update && apt install maven -y

RUN mvn install -DskipTests

FROM eclipse-temurin:8
WORKDIR /usr/app
COPY --from=build_image /usr/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar
EXPOSE 9000
ENTRYPOINT ["java","-jar","book-work-0.0.1.jar"]

