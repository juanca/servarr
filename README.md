# servarr

https://wiki.servarr.com/

## vpn

1. Make user file `./vpn/config/user` and insert credential
2. Make password file `./vpn/config/pass`  and insert credential

### docker

1. Create network volume with following directory structure:
    ```
    network-volume/
      downloads/
      media/
        anime/
        books/
        movies/
        music/
        tv/
        xxx/
    ``` 
2. Boot up: `docker-compose up`
3. Verify vpn logs for successful connection: `docker-compose logs vpn`

### [qbittorrent](http://localhost:8080)

1. Update Settings > Downloads > Saving Management 
   - Default Torrent Management Mode: `Automatic`
   - When Torrent Category changed: `Relocate torrent`
   - When Default Save Path changed: `Relocate affected torrent`
   - When Category Save Path changed: `Relocate affected torrent`
   - Use Subcategories
   - Default save path: `/data/downloads`
   - Keep incomplete torrents in: `/data/downloads/incomplete`
2. Set reasonable global rate limits in Settings > Speed
3. Test IP address with https://ipleak.net/

### [prowlarr](http://localhost:9696)

1. Add public indexers
2. Add apps while doing their own setup below

### [lidarr](http://localhost:8686)

1. Add [qBittorrent download client](http://vpn:8080) and use `music` category
3. Add root path (under settings > media management) for `/data/media/music`
4. Rename tracks (under settings > media management) to organize music

### [radarr](http://localhost:7878)

1. Add [qBittorrent download client](http://vpn:8080) and use `movies` category
2. Add root path (under settings > media management) for `/data/media/movies`
3. Delete all the Settings > Profiles (except "Any")

### [readarr](http://localhost:8787)

1. Add [qBittorrent download client](http://vpn:8080) and use `books` category
3. Add root path (under settings > media management) for `/data/media/books`

### [sonarr](http://localhost:8989)

1. Add [qBittorrent download client](http://vpn:8080) and use `tv` category
3. Add root path (under settings > media management) for `/data/media/tv`
4. Add root path (under settings > media management) for `/data/media/anime`
5. Delete all the Settings > Profiles
6. Remove any "remux" qualities in the Any profile (cannot be deleted unfortunately)

### recyclarr

1. Open and change the API key in `./recyclarr/configs/sonarr-v4.yml`
2. Open and change the API key in `./recyclarr/configs/radarr.yml`
3. Sync the configurations with `docker compose run -it recyclarr sync --debug`

### [whisparr](http://localhost:6969)

1. Add [qBittorrent download client](http://vpn:8080) and use `xxx` category
3. Add root path (under settings > media management) for `/data/media/xxx`

### [plex](http://localhost:32400/)

1. If on OSX, install the plex app. Otherwise follow below:
1. Get claim token from https://plex.tv/claim
2. Set environment variable in docker-compose.yml with `PLEX_CLAIM=`
3. Restart plex container and inspect logs
4. Open lidarr > Settings > Connect: plex at `host.docker.internal` for music
5. Open radarr > Settings > Connect: plex at `host.docker.internal` for movies
4. Open sonarr > Settings > Connect: plex at `host.docker.internal` for tv shows

### [stash](http://localhost:9999/)

1. Set blob/database to filesystem with path `/stash/blobs/`
2. Run Tasks > Scan library with all the generate features turned on
3. Set Metadata Providers > Endpoint from [profile information](https://stashdb.org)
4. Run Tasks > Identify without any of the match guards
5. Open whisparr > Settings > Connect: stash at `host.docker.internal`

### [overseerr](http://localhost:5055)

1. Connect to plex media server with `host.docker.internal`
2. Connect to radarr with `http://radarr`
3. Connect to sonarr with `http://sonarr`
   - Choose appropriate root folder and quality profile
   - Choose appropriate anime root folder and anime quality profile
4. TODO: multiple instances of each for subtitles and/or anime?
