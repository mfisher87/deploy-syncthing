# My Syncthing deployment

This repo helps me set up a new Syncthing installation quickly.

Syncthing is the tool I reach for to solve this problem:

![XKCD 949: File Transfer - Randall Munroe](https://imgs.xkcd.com/comics/file_transfer.png)

> _[XKCD 949: File Transfer](https://xkcd.com/949) - Randall Munroe_


## Quickstart

```
docker compose up
```

Visit <http://localhost:8384> in a browser to view the GUI.


## Installation

```
git clone {this_repo_url} ~/Sync
```


## Data directories

If these dirs don't pre-exist, Docker will make them owned by `root`, which will prevent
Syncthing from starting. That's why they exist in this repo.

> [!WARNING]
>
> The Syncthing container runs as user 1000, this matches the first user created in most
> Linux distros. I need to add more docs for the case where the host user is not 1000.


### `config/`

Where config for this Syncthing instance goes. Includes information like client ID, so
it **should not be committed**.


### `data/`

Where actual synced data goes.
