# My Syncthing deployment

This repo helps me set up a new Syncthing installation quickly. Alternately,
[download a compiled release from GitHub](https://github.com/syncthing/syncthing/releases).

Syncthing is the tool I reach for to solve this problem:

![XKCD 949: File Transfer - Randall Munroe](https://imgs.xkcd.com/comics/file_transfer.png)

> _[XKCD 949: File Transfer](https://xkcd.com/949) - Randall Munroe_


## Installation

```
git clone {this_repo_url} ~/Sync
```

> [!NOTE]
> 
> Syncthing normally syncs data in and out of `~/Sync`, so to me it seemed easiest to
> remember to work entirely in that directory, and sync data in and out of
> `~/Sync/data`. I don't think this is canonical, it just helps me with cognitive load.


## Usage

```
docker compose up
```

Visit <http://localhost:8384> in a browser to view the GUI.


## Data directories

If these dirs don't pre-exist, Docker will make them owned by `root`, which will prevent
Syncthing from starting. That's why they exist in this repo.

> [!WARNING]
>
> The Syncthing container runs as user 1000, this matches the first user created in most
> Linux distros. I need to add more docs for the case where the host user is not 1000.


### `config/`

Where config for this Syncthing instance goes. Includes information like client ID, so
it **should not be committed**. A `.gitignore` file in this directory is meant to
prevent that.


### `data/`

Where actual synced data goes. These files might be big, or secret. They're definitely
irrelevant to this repo, so they **should not be committed**. A `.gitignore` file in
this directory is meant to prevent that.

> [!NOTE]
>
> The `.gitignore` file will be synced to any devices that share Default Folder.
