FROM openjdk:8-jre-alpine

RUN apk add --update bash && rm -rf /var/cache/apk/*

RUN mkdir -p /var/www/springping

WORKDIR /var/www/springping

RUN wget http://madariaga1.claro.amx:8081/artifactory/libs-release-local/com/claro/amx/ums/ums-backend/3.1.7/ums-backend-3.1.7.jar -O springping.jar

EXPOSE 8080

CMD ["java","-Djava.security.egd=file:/dev/./urandom", "-Dserver.port=8080", "-jar", "springping.jar"]