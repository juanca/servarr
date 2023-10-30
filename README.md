# servarr

https://wiki.servarr.com/

## setup

1. Make files and insert credentials to PIA
   - `vpn/config/user` and `vpn/config/pass`
   - Check vpn logs for successful connection
1. Boot up: `docker-compose up`
1. Setup download path and upload limits for [transmission](http://localhost:9091)
   - Download into `/data/downloads
1. Setup [prowlarr](http://localhost:9696)
   - Indexers
   - Settings > Apps (e.g. http://lidarr:8686)
1. Setup apps
   - Download client with category/tags (i.e. http://vpn:9091)
     - [lidarr](http://localhost:8686): `music`
     - [radarr](http://localhost:7878): `movies`
     - [readarr](http://localhost:8787): `books`
     - [sonarr](http://localhost:8989): `tv`
     - [whisparr](http://localhost:6969): `xxx` 
   - Settings > Media management > Root path
     - [lidarr](http://localhost:8686): `/data/media/music`
     - [radarr](http://localhost:7878): `/data/media/movies`
     - [readarr](http://localhost:8787): `/data/media/books`
     - [sonarr](http://localhost:8989): `/data/media/tv`
     - [whisparr](http://localhost:6969): `/data/media/xxx`
1. Setup [plex](http://localhost:32400/web) (Note: possibly use a claim token)
1. Setup [overseerr](http://localhost:5055): unified requests for tv and movies interface 
1. Setup [jellyfin](http://localhost:8096)
