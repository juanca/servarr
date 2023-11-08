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
    incomplete/
    complete/
      books/
      movies/
      music/
      tv/
      xxx/
  media/
    books/
    movies/
    music/
    tv/
    xxx/
``` 
2. Boot up: `docker-compose up`
3. Verify vpn logs for successful connection: `docker-compose logs vpn`

### [torrents](http://localhost:9091)

1. Set download path to `/data/downloads` for proper symlink paths. Shares parent directory with `/data/media`
2. Set a reasonable download limit
3. Set a reasonable upload limit  

### [prowlarr](http://localhost:9696)

1. Add public indexers
2. Add apps while doing their own setup below

### [lidarr](http://localhost:8686)

1. Add download client pointed to http://vpn.9091
2. Use `music` category to avoid seeing irrelevant downloads
3. Add root path (under settings > media management) for `/data/media/music`

### [radarr](http://localhost:7878)

1. Add download client
2. Use `movies` category to avoid seeing irrelevant downloads
3. Add root path (under settings > media management) for `/data/media/movies`

### [readarr](http://localhost:8787)

1. Add download client
2. Use `books` category to avoid seeing irrelevant downloads
3. Add root path (under settings > media management) for `/data/media/books`

### [sonarr](http://localhost:8989)

1. Add download client
2. Use `tv` category to avoid seeing irrelevant downloads
3. Add root path (under settings > media management) for `/data/media/tv`

### [whisparr](http://localhost:6969)

1. Add download client
2. Use `xxx` category to avoid seeing irrelevant downloads
3. Add root path (under settings > media management) for `/data/media/xxx`

### [plex](http://localhost:32400/)

1. Get claim token from https://plex.tv/claim
2. Set environment variable in docker-compose.yml with `PLEX_CLAIM=`
3. Restart plex container and inspect logs

### [overseerr](http://localhost:5055)

???

### [jellyfin](http://localhost:8096)

???
