
## Docker

![docker](imgs/docker.png)

<div style="text-align:justify;">
Docker is an open-source platform designed to automate the deployment, scaling, and management of applications in lightweight containers. Containers allow developers to package an application with all its dependencies and libraries, ensuring consistent performance across different environments. Docker simplifies and accelerates the workflow from development to production by providing tools for creating, distributing, and running containers. It supports isolation, scalability, and rapid deployment, making it a popular choice for modern software development and DevOps practices.
</div>
<div style="text-align:justify;">
The best way to manage docker is through Portainer. Portainer is a lightweight management UI which allows you to easily manage your Docker environments. It can be used to manage Docker containers, images, networks, and volumes from a simple web interface.
</div>

### Installing Portainer

```bash
docker run -d -p 9443:9443 -p 8000:8000 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

```
Once portainer installed these are the image I usually work with.

| Category | Name | Description | URL | 
| --- | --- | --- | --- | 
| Dashboard | Heimdall | An application dashboard and launcher. | https://hub.docker.com/r/linuxserver/heimdall | 
| Home Assistant | Home Assistant | Open-source home automation platform. | https://hub.docker.com/r/homeassistant/home-assistant | 
|  | openHAB | Vendor and tech agnostic open-source home automation software. | https://hub.docker.com/r/truecharts/openhab | 
| Low Code Frameworks | Appsmith | Open-source platform to build internal tools. | https://hub.docker.com/r/bitnami/appsmith | 
|  | Budibase | Low code platform for building internal tools, with a focus on speed and simplicity. | https://hub.docker.com/r/budibase/budibase | 
|  | Directus | Open data platform for managing SQL database content. | https://hub.docker.com/r/truecharts/directus | 
|  | Metabase | Open-source business intelligence tool. | https://hub.docker.com/r/truecharts/metabase | 
|  | MotorAdmin | Admin panel for managing databases. | https://hub.docker.com/r/motoradmin/motoradmin | 
|  | NocoBase | Open-source no-code/low-code platform. | https://hub.docker.com/r/nocobase/nocobase | 
|  | NocoDB | Open-source no-code database and Airtable alternative. | https://hub.docker.com/r/truecharts/nocodb | 
|  | Saltcorn | Platform for building database-driven applications without writing code. | https://hub.docker.com/r/saltcorn/saltcorn | 
|  | ToolJet | Open-source low-code framework to build internal tools. | https://hub.docker.com/r/tooljet/tooljet-ce | 
| Monitoring | Grafana | Open-source analytics and monitoring platform. | https://hub.docker.com/r/grafana/grafana | 
|  | Loki | Log aggregation system designed to work with Grafana. | https://hub.docker.com/r/grafana/loki | 
|  | Netdata | Real-time performance monitoring, in-depth metrics collection, and visualization. | https://hub.docker.com/r/truecharts/netdata | 
|  | Uptime Kuma | Self-hosted monitoring tool. | https://hub.docker.com/r/truecharts/uptime-kuma | 
|  | Watchtower | Automatically updates running Docker containers. | https://github.com/containrrr/watchtower | 
| Others | Nuts Node | Decentralized, self-sovereign identity system. | https://hub.docker.com/r/nutsfoundation/nuts-node | 
|  | OpenBooks | Open-source project for managing personal finances. | https://hub.docker.com/r/evanbuss/openbooks | 
|  | PhotoPrism | AI-powered app for browsing, organizing, and sharing photo collections. | https://hub.docker.com/r/photoprism/photoprism | 
|  | Radarr | A movie collection manager for Usenet and BitTorrent users. | https://hub.docker.com/r/linuxserver/radarr | 
|  | Sonarr | PVR for Usenet and BitTorrent users, used for downloading and managing TV shows. | https://hub.docker.com/r/linuxserver/sonarr | 
| Proxy | Traefik | Open-source Edge Router that makes deploying microservices easy. | https://hub.docker.com/_/traefik | 
|  | GoAccess | Real-time web log analyzer and interactive viewer that runs in a terminal in *nix systems. | https://hub.docker.com/r/truecharts/goaccess |
