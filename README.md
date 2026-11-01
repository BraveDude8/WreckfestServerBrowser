# Wreckfest Enhanced Server Browser

Find out which mods a Wreckfest server needs, set them up in the right order, and get pinned to that server in one click.

For Wreckfest 1 on Steam with normal Workshop mods. An unofficial fan tool, not made or endorsed by the owners of Wreckfest.

<img width="750" alt="wreckfest server browser 1" src="https://github.com/user-attachments/assets/e7c5c81e-bfd2-426f-893a-7ce3bb1c3109" />

<img width="750" alt="image-1793547372449" src="https://github.com/user-attachments/assets/bf7a5454-517a-4f4d-a5b9-7f5d58798361" />

<img width="750" alt="image-1793547372449 2" src="https://github.com/user-attachments/assets/e09a4394-f7fc-45a0-a7c9-b7206c27ec42" />

## Why this exists

A modded server only lets you in if your enabled mods give exactly the same "signature" number as the server's. Where two mods contain the same file, their order changes that number too. The game shows you a red X but never says which mods it wants.

This tool works out the mods and the order, then sets up your Mod Manager list for you.

## Getting started

Download the zip from Releases, extract it, and keep the three exes together in one folder. There is nothing to install. It needs Windows and the Steam version of Wreckfest 1.

1. Run `WfEnhancedServerBrowser.exe` and press **LAUNCH WRECKFEST**.
2. Open the game's server browser and scroll. The servers appear in the tool as the game lists them.
3. Click the server selector, type to narrow the list, and pick a server. A green **JOIN** badge means your mods already match it.
4. Press **SET ME UP FOR THIS SERVER**. If the game is open, close it. The tool writes your mod list as soon as the game exits, then starts the game again.
5. In the Internet tab of the server browser, the server is starred and pinned at the top. Select it and join.

## Features

- **Works out a server's mods.** It uses the server's signature, any mods the server names, and the mods you have installed.
- **Solves the load order** and writes your Mod Manager list, keeping a backup first.
- **Which can I join?** Checks every modded server at once. This takes a few minutes the first time.
- **Get these mods.** Subscribes to the mods a server needs through Steam, but only when you press the button, then watches for the download.
- **Mod lists.** Shows every list the tool knows and where each one is played.
- **Profiles and share codes.** Save named mod lists, including Stock, and swap them with friends as short codes.
- **Handles mod updates.** When Steam updates a mod, known lists get their new signature. If a server is still on an older version, the tool says so and tells you when your mods fit.
- **Filters and favourites.** Show only servers with people on, ones you could join with a download, favourites, or ones without a password.

## Badges

| Badge | Meaning |
|---|---|
| JOIN | Your enabled mods match this server right now |
| NEED | It needs mods you don't have |
| STOCK | No mods: SET ME UP turns all your mods off |
| MODS | Any other modded server: pick it to see whether you have its mods |
| CAN'T | It shows 0 mods but its data isn't stock, so no mod list can match it |

## What it changes on your PC

- **`modlist.mods`** in `Steam\userdata\<you>\228380\local\wreckfest\`. It saves a backup beside the file first and never writes while Wreckfest is running.
- **`career.cres`**, only to add the server to your in-game favourites when SET ME UP starts the game. The game is closed at that point, and a backup is kept beside the file (newest 5). If the file isn't a version the tool knows, it is left alone and the log asks you to star the server yourself.
- **Its own files** in `%LOCALAPPDATA%\WfJoinHelper\` and `%APPDATA%\WfJoinHelper\`.
- **One new file in Documents** each time you use an Export button.

**RESTORE** puts back the list from before your last SET ME UP. It goes back one step only. Older lists stay as `modlist.mods.joinhelper-<time>.bak` files next to `modlist.mods`.

To remove the tool, delete the exes and the two `WfJoinHelper` folders.

## What it connects to

Nothing is hosted and nothing is uploaded.

- With **Online lookups** ticked, it asks the public Steam Web API for mod titles, sizes, update times and collection contents.
- **GET THESE MODS** runs `WfEnhancedServerBrowserSteam.exe`, which subscribes through the `steamclient64.dll` in your Steam folder and briefly shows you as in Wreckfest on Steam. The tool never unsubscribes anything.

## Antivirus warnings

Some antivirus engines flag these exes. On VirusTotal, the v1.0.1 main exe scored 5 of 71, mostly from machine-learning and heuristic detections. The exes are small, unsigned .NET programs, and they start the game and edit a save file, which may be why, though that can't be proven from the results. Compare your download with `SHA256SUMS.txt`, and don't run it if you aren't comfortable with that.

## For server admins

Put one of these in your server's welcome message so players' tools can read it:

```
collection=<Workshop collection id>
mods="id;id;id"
```

A collection is best: it is short and can hold any number of mods. Sort it in Mod Manager order. `mods=` fits up to about 22 ids.

To print your signature and a ready-to-paste welcome line, list your mod ids in Mod Manager order, top to bottom:

```
WfEnhancedServerBrowserCli.exe admin <your mod ids>
```

## Limits

- It can only identify mods you have installed, unless the server or a known list names them.
- A different version of a mod gives a different signature. Steam only downloads the newest version, so you can't join a server on an older one until it updates.
- You still press join in the game. Wreckfest has no way to join a dedicated server from outside the game.
- Mods made only of skins or textures don't change the signature, so they are never needed to pass the check.

The full manual is `README.txt` in the download.
