# download release jar
FROM mwendler/wget as download
WORKDIR /downloads
ENV VERSION=1.8.2
ARG JAR_NAME=sentinel-dashboard-${VERSION}.jar
ARG RELEASE_DOWNLOAD_URL=https://github.com/alibaba/Sentinel/releases/download/${VERSION}/${JAR_NAME}
RUN wget --no-check-certificate --content-disposition ${RELEASE_DOWNLOAD_URL} -O sentinel-dashboard.jar

# build image
FROM openjdk:8u201-jre-alpine3.9
WORKDIR /home/sentinel
ENV VERSION=1.8.2
ENV csp_sentinel_dashboard_server=localhost:8080
ENV project_name=sentinel-dashboard
LABEL maintainer="qkssk1711@163.com"
LABEL release=${VERSION}
COPY --from=download /downloads/sentinel-dashboard.jar .
CMD java -Dcsp.sentinel.dashboard.server=$csp_sentinel_dashboard_server -Dproject.name=$project_name -jar sentinel-dashboard.jar