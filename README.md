# rVclient Community & Private Servers

Host your own Rumbleverse server with rVclient.

| | Private server | Community server |
|---|---|---|
| Who plays on it | You + your friends | Everyone in your region |
| Where it runs | Your own PC | A VPS or dedicated server |
| How people join | Friends on your Tailscale or Radmin VPN network see it in their launcher | Public matchmaking (after we approve it), tagged **Community** in the launcher |

## Get started
1. Download **`RVServer-Setup.zip`** from the [latest release](../../releases/latest) and extract it anywhere.
2. Read `README.txt` inside, then double-click `Setup-RVServer.bat`.

The same files are in the [`RVServer-Setup`](RVServer-Setup) folder of this repo.

On a home internet connection setup always makes a **private** server - public community servers need a VPS or dedicated server.

## Good to know
- You need **your own copy of Rumbleverse** - we never provide game files.
- You need the **rVclient launcher 1.7.48 or newer**.
- Your game is never changed - it keeps starting from the launcher, even while your server runs.
- Updates come by themselves; to remove a server, run `Uninstall-RVServer.bat` (or Remove in the launcher for a private server).
- **Community servers:** open UDP **7777-7781** and **7877-7881** (warm spares) in your provider's firewall or router. Plan about **4 GB RAM per Battle Royale mode** (two servers each, about 2 GB per server with memory saving).

## What your community server does by itself
- **Warm spare servers** - every Battle Royale mode has a second server ready on port + 100. One lobby is open at a time; the moment a match launches, the next lobby opens on the other server, so players never wait for a reboot.
- **Auto barge countdown** - the lobby countdown follows how fast players arrive: busy = longer, so lobbies fill toward 40 players; quiet = 120 s. Set the shortest / longest yourself in rV Modes.
- **Memory saving** (about 2 GB less RAM per server) and **bots on teams** in Duos / Trios / Squads.

Everything is a setting in **rV Modes** (gear button) - on by default.

## Credits
Fixes contributed by community server hosts - thank you!

| Who | What | In server |
|---|---|---|
| **MCha** (Asia community servers, Japan) | Found the regular server freezes on slower machines - the server searched all ~550,000 game objects every 30-60 s in a single frame (150-350 ms) - and wrote a fix that skips the objects that didn't change. Built into the server as **Fast object searches** (on by default, a setting in the admin panel). | 2026.10.8.2 |
| **MCha** (Asia community servers, Japan) | **Memory saving** (frees the graphics and sound data a server never uses - about 2 GB less RAM per server), **bots on teams** (a Duos / Trios / Squads match with only one real team plays instead of ending at launch), crash fixes for special-character names and broken configs, start-up map loading fixes, a spectate update cap, a log queue and more reliable backend calls. | 2026.10.10.2 |

Found a problem and have a fix? Share it in the rVclient Discord - we test it, build it in and credit you here.

### Built on
| Project | Used for |
|---|---|
| [**UE4-Librarian**](https://github.com/Aeyth8/UE4-Librarian) by **Aeyth8** | The DLL loader (`dxgi.dll` + `DList.ini`) that loads the server's mods into the game server, and Client.dll into players' games |
| [**Unreal Mod Unlocker**](https://github.com/IllusorySoftware/UnrealModUnlocker-Public) by **Illusory Software** | The proxy code inside that loader, and the server's loose-file mod loading (`UnrealModPlugins/UnrealModUnlocker.dll`) |

Questions? Ask in the rVclient Discord.
