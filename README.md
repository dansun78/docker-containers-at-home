# Running Docker Containers on a Raspberry Pi 4 at Home

This repository includes Docker Compose files that I used to define services
running on a Raspberry Pi 4 at home for my personal use.

Configurations for each service are declared as environment variables in its
Docker Compose file and are expected to be passed to Docker Compose via its
default environment file, `.env`.

## Plex

This Docker Compose file is based on the example provided in the official Docker
image of [Plex Media server](https://github.com/plexinc/pms-docker). However it
uses the image, which is built by myself, because Plex does not release an
`arm32v7` image on Docker Hub

### Environment Variables / Configurations:

- `TZ` - Set the timezone inside the container. For example: Pacific/Auckland.
  The complete list can be found
  [here](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
- `PLEX_CLAIM` - The claim token for the server to obtain a real server token.
  If not provided, server will not be automatically logged in. If server is
  already logged in, this parameter is ignored. You can obtain a claim token to
  login your server to your plex account by visiting https://www.plex.tv/claim
- `PLEX_UID`- The user id of the plex user created inside the container.
- `PLEX_GID` - The group id of the plex user created inside the container.
- `CONFIG_PATH` - The path on the host where you wish Plex Media Server to store
  its configuration data.
- `DATA_PATH` - The path on the host where you wish Plex Media Server to obtain
  media files the via the `/data` direcotry insider the container.

## Transmission

This Docker Compose file is based on the sample provided by the a
[Docker image](https://registry.hub.docker.com/r/linuxserver/transmission)
published on Docker Hub.

### Environment Variables / Configurations:

- `PUID` - The user id on the host to run the container.
- `PGID` - The group id on the host to run the container.
- `ADMIN_USER` - The administrator's user name when interacting with Transmission insider the container. 
- `ADMIN_PASS` - The administrator's password when interacting with Transmission insider the container.
- `CONFIG_PATH` - The path on the host where Transmission to store its configuration and log files.
- `DOWNLOAD_PATH` - The path on the host where Transmission to stored downloaded files.
- `WATCH_PATH` - The path on the host where Transmission to monitor torrent files for starting new downloads. 

