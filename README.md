# Docker Containers

[![Docker Version](https://images.microbadger.com/badges/version/miguel1993/plex-sync.svg)](https://microbadger.com/images/miguel1993/plex-sync) [![Docker Image](https://images.microbadger.com/badges/image/miguel1993/plex-sync.svg)](https://microbadger.com/images/miguel1993/plex-sync) [![Docker Pulls](https://img.shields.io/docker/pulls/miguel1993/plex-sync.svg)](https://microbadger.com/images/miguel1993/plex-sync) [![Docker Stars](https://img.shields.io/docker/stars/miguel1993/plex-sync.svg)](https://microbadger.com/images/miguel1993/plex-sync) [![License MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

[`plex-sync`](https://github.com/jacobwgillespie/plex-sync) running in a container as a cron job.

Fork from [`https://github.com/patsissons/docker-plex-sync`](https://github.com/patsissons/docker-plex-sync) but with the node memory limit increased to 4GB for syncing larger libraries.

## Usage

* `SECTION_MAPS` is the important environment variable to set, it uses the same syntax that `plex-sync` uses, but allows multiple mappings to be configured by separating them with a `|` as shown in the example below.
* `CRON_SCHEDULE` allows you to configure a non-default schedule to run the sync (default is every hour, `0 * * * *`)
* `INITIAL_RUN` will run `plex-sync` before starting cron if set to anything.

```sh
docker run -d -e SECTION_MAPS='xxxxxx@10.0.1.5/1 zzzzzz@10.0.1.10/3 | xxxx@10.0.1.6:32401/1,r https://yyyy@10.0.1.7/3,w zzzz@10.0.1.8/2,rw' -e CRON_SCHEDULE='*/5 * * * *' -e INITIAL_RUN=true miguel1993/plex-sync
```
