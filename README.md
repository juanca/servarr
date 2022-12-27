# servarr

https://wiki.servarr.com/

## setup

1. Credentials to PIA in files (check vpn logs for successful connection)
1. Boot up: `docker-compose up`
1. Setup download and upload limits for [transmission](http://localhost:9091)
1. Setup [prowlarr](http://localhost:9696)
   - Indexers
   - Apps
1. Setup apps
   - Download client with tags
   - Settings > Media management > Root path
   - [lidarr](http://localhost:8686): tag `music`, path: `/music`
   - [radarr](http://localhost:7878): tag `movies`, path `/movies`
   - [readarr](http://localhost:8787): tag `books`, path `/books`
   - [sonarr](http://localhost:8989): tag `tv`, path `/tv`
