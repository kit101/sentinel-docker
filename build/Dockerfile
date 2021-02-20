# download release jar
FROM mwendler/wget as download
WORKDIR /downloads
ENV VERSION=1.8.1
ARG JAR_NAME=sentinel-dashboard-${VERSION}.jar
ARG RELEASE_DOWNLOAD_URL=https://github.com/alibaba/Sentinel/releases/download/${VERSION}/${JAR_NAME}
RUN wget --no-check-certificate --content-disposition ${RELEASE_DOWNLOAD_URL} -O sentinel-dashboard.jar && ls

# build image
FROM openjdk:8u201-jre-alpine3.9
WORKDIR /home/sentinel
ENV VERSION=1.8.1
ENV JAVA_OPTS=
LABEL maintainer="qkssk1711@163.com"
LABEL release=${VERSION}
COPY --from=download /downloads/sentinel-dashboard.jar .
CMD [ "java", "-jar", "sentinel-dashboard.jar" ]