# arm-cadvisor-nodeexporter
Unofficial cAdvisor &amp; Node Exporter image for ARM (Raspberry Pi).

Test Environment: **Raspbian Buster** on **Raspberry Pi 4 Model B**

## Quickstart
```bash
$ git clone https://github.com/freckie/dockerfiles
$ cd dockerfiles/arm-cadvisor-nodeexporter
$ sudo docker-compose up -d
```

## Build cAdvisor only
```bash
$ git clone https://github.com/freckie/dockerfiles
$ cd dockerfiles/arm-cadvisor-nodeexporter/arm-cadvisor
$ sudo docker build --tag <your-tag-name> ./
```
