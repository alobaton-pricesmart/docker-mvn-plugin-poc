
FROM openjdk:11
ARG APP_VERSION
ENV APP_VERSION=${APP_VERSION}
EXPOSE 8080
ADD maven/docker-mvn-plugin-*.jar /opt/docker-mvn-plugin.jar
RUN sh -c 'touch /opt/docker-mvn-plugin.jar' && \
    addgroup -S appuser && \
    adduser -S -g appuser appuser && \
    apk add --update --no-cache bash coreutils curl jq && \
    rm -rf /var/cache/apk/*
USER appuser
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/opt/docker-mvn-plugin.jar"]