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

## Credits
Fixes contributed by community server hosts - thank you!

| Who | What | In server |
|---|---|---|
| **MCha** (Australia community server) | Found the regular server freezes on slower machines - the server searched all ~550,000 game objects every 30-60 s in a single frame (150-350 ms) - and wrote a fix that skips the objects that didn't change. Built into the server as **Fast object searches** (on by default, a setting in the admin panel). | 2026.10.8.2 |

Found a problem and have a fix? Share it in the rVclient Discord - we test it, build it in and credit you here.

Questions? Ask in the rVclient Discord.
