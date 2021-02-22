# Alibaba Sentinel Docker Image Build（阿里巴巴分布式系统的流量防卫兵Docker镜像）
[![Build Status](https://cloud.drone.io/api/badges/kit101/sentinel-docker/status.svg?ref=refs/tags/1.8.1)](https://cloud.drone.io/kit101/sentinel-docker)
## Files Tree
```bash
├── README.md 
├── build       # build workspace
│   └── Dockerfile
├── envs        # example configurations
│   └── simple.env
└── examples    # example docker-compose files
    └── simple-compose.yaml
```
## Docker Build
```bash
git clone https://github.com/kit101/sentinel-docker
cd sentinel-docker
docker build -f build/Dockerfile -t kitkit/sentinel-dashboard .
```
## Usage
### docker run
```bash
# csp_sentinel_dashboard_server default: localhost:8080
# project_name default: sentinel-dashboard
# set env change csp_sentinel_dashboard_server or project_name
# docker container default command `java -Dcsp.sentinel.dashboard.server=$csp_sentinel_dashboard_server -Dproject.name=project_name -jar sentinel-dashboard.jar`
docker run --name sentinel-dashboard \
  -e server_port=8718 \
  -e csp_sentinel_dashboard_server=localhost:8718 \
  -e sentinel_dashboard_auth_password=sentinel \
  -p 8718:8718 \
  kitkit/sentinel-dashboard
# custom start command
docker run --name sentinel-dashboard \
  -e server_port=8718 \
  -p 8718:8718 \
  kitkit/sentinel-dashboard java -Dcsp.sentinel.dashboard.server=localhost:8718 -jar sentinel-dashboard.jar
```
### docker-compose up
```bash
git clone https://github.com/kit101/sentinel-docker.git
cd sentinel-docker
docker-compose -f examples/simple-compose.yaml up
```

## Other

[Dockerfile](https://github.com/kit101/sentinel-docker)

[Application source code](https://github.com/alibaba/Sentinel)