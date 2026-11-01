---
title: 'Dedicated Server Tutorial'
description: How to setup a ZMR dedicated server
date: 2026-11-01
---

## Foreword

If you just want to goof around with friends, a listen server (Create Server in-game) is probably good enough. Just remember to look at [the last section](#whats-next) for further customization.

## SteamCMD

Start with installing SteamCMD. Use [this page](https://developer.valvesoftware.com/wiki/SteamCMD) for guidance.

## Install Source SDK Base 2013 Dedicated Server

NOTE: The one you download through Steam UI probably won't work. You should use SteamCMD.

Run SteamCMD and run the following commands:

```
force_install_dir my2013folder
login anonymous
app_update 244310
```

## External dependencies (Linux)

Linux dedicated server files are missing some dependencies, which you need to get from TF2 dedicated server repository:
`bin/linux64/libsteam_api.so`, `srcds_linux64` and `srcds_run_64`. You can either download the entire thing through SteamCMD (app id `232250`) or [use other means](https://forums.alliedmods.net/showpost.php?p=2837994&postcount=2) to download just those three files.

The game also needs to see `steamclient.so`, which comes with SteamCMD:

```bash
# Might be somewhere else depending how you installed SteamCMD.
ln -s  ~/.local/share/Steam/steamcmd/linux64 ~/.steam/sdk64
```

## Install mod dedicated server files

Download the dedicated server files and place the `zombie_master_reborn` directory in `my2013folder`.

## Run

```bash
cd my2013folder
./srcds_run_64 -game zombie_master_reborn +map zm_docksofthedead
```

## What's next

### Game server account

If you intend to make the server public, you need to attach a Steam account to the server. You can do so [here](https://steamcommunity.com/dev/managegameservers). Set the app id to `243750`.

### Navigation meshes

Generally, most custom maps do not pack the required navigation meshes for zombie movement. You can find a community maintained repository [here](https://github.com/zm-reborn/zmr-map-configs).

### SourceMod

ZMR does not work with SourceMod out of the box. You need to install SourceMod gamedata for full functionality. You can get them [here](https://github.com/zm-reborn/zmr-sm).
