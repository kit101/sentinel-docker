# Alibaba Sentinel Docker Image Build（阿里巴巴分布式系统的流量防卫兵Docker镜像）
[![Build Status](https://cloud.drone.io/api/badges/kit101/sentinel-docker/status.svg)](https://cloud.drone.io/kit101/sentinel-docker)
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
docker build -f build/Dockerfile kit101/sentinel-dashboard .
```
## Usage
### docker run
```bash
docker run --name sentinel-dashboard \
  -e server_port=8718 \
  -e csp_sentinel_dashboard_server=localhost:8718 \
  -e sentinel_dashboard_auth_password=sentinel \
  -p 8718:8718 \
  kitkit/sentinel-dashboard
```
### docker-compose up
```bash
git clone https://github.com/kit101/sentinel-docker.gits
cd sentinel-docker
docker-compose -f examples/simple-compose.yaml up
```