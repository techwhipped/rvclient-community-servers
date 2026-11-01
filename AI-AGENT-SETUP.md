# Host an rVclient server with an AI agent's help

This file is written **for an AI agent** (Claude Code, Codex, Cursor, ...) helping someone host a
Rumbleverse server with rVclient - a **private** server for them and their friends, or a
**community** server on a VPS. The agent checks the machine, walks the person through the setup
tool and helps when something goes wrong.

**How to use it:** download this repo (or the `RVServer-Setup.zip` release), open the folder in
your agent and give it the prompt at the end.

---

## 0. Ground rules for the agent

1. **Never download, upload or share Rumbleverse game files.** The person uses *their own* copy;
   setup finds the one their rVclient launcher uses.
2. **Never share or paste `setup-state.json`** from the server folder - it holds the server's key.
   The same goes for the 30-minute setup code: it is for this setup only.
3. **The person runs the setup and uninstall scripts themselves.** They ask questions and need an
   administrator prompt; explain each question, do not answer them on the person's behalf.
4. **The game and the servers are the same exe** (`RumbleverseClient-Win64-Shipping.exe`). Stop
   processes **by full path** (the server folder), never by name - killing by name also closes the
   person's game.
5. **Never edit the server's files by hand.** Settings live in **rV Modes**; updates arrive by
   themselves. Hand edits are overwritten or break the next update.
6. **Logs before fixes.** Read what the server and setup actually said before suggesting anything.
7. Do not open ports, change router settings or install VPN software without asking first.

---

## 1. Private or community?

| | Private server | Community server |
|---|---|---|
| Who plays | the person + friends | everyone in the region, after approval |
| Runs on | their own PC | a VPS or dedicated server |
| Friends join over | Tailscale or Radmin VPN (same network) | public matchmaking |
| Ports | nothing to forward | UDP **7777-7781** and **7877-7881** open in the provider's firewall |

On a home internet connection setup always makes a **private** server.

## 2. Check the machine

- Windows 10/11 or Windows Server 2019+, 64-bit.
- RAM: about **2 GB per server**. A community server runs two servers per Battle Royale mode (the
  warm spare), so about **4 GB per mode**. A private server runs one per mode.
- Disk: about 15 GB if setup copies the game, about 1 GB if it links it.
- The newest rVclient launcher, signed in.
- Optional and harmless: **right-click `RVServer-Setup\Host-Check.ps1` > Run with PowerShell**. It
  rates CPU, RAM, disk and network and changes nothing. Read its result to the person.

Tell the person plainly if the machine is too small for what they want.

## 3. Set it up (the person runs it, you explain)

1. **Private only:** in the rVclient launcher, *Server Status > My private servers > Set up a
   private server*. Keep the code it shows (valid 30 minutes).
2. Double-click **`RVServer-Setup\Setup-RVServer.bat`**. It asks:
   - which drive (it suggests the game's drive);
   - the setup code (private) or a Discord name (community, so the team can reach them);
   - **C** = copy the game files (recommended, fully separate) or **L** = link them (no extra space).
   Then it asks for administrator rights (firewall rules and optional auto-start).
3. Done:
   - **Private:** the server shows in the launcher under *My private servers* - press **Join**.
     Friends on the same Tailscale / Radmin network see it too; *Share...* adds them by rVclient name.
   - **Community:** it is registered and **waiting for approval**, then joins matchmaking by itself.

Setup never moves or changes the person's game. It keeps starting from the launcher as normal.

## 4. Managing it

The **"rV Modes (server)"** desktop shortcut: turn modes on/off, restart a mode, see the review
status, update. The gear button holds each mode's settings (bots, barge countdown, warm spare,
memory saving, bots on teams...). After an update, restart rV Modes' servers (or reboot) once.

## 5. When something goes wrong

| Symptom | Check |
|---|---|
| Setup stops with an error | read the text it printed; run it again - it is safe to repeat |
| Private server not in the launcher | same rVclient account? the setup code was used within 30 minutes? |
| Friends can't see or join it | both PCs on the same Tailscale / Radmin network and connected? |
| Community server never gets players | still waiting for approval (rV Modes shows it); UDP 7777-7781 and 7877-7881 open at the provider, not only in Windows |
| A mode keeps restarting | free RAM (about 2 GB per server); rV Modes' log for that mode; `crash_trace_*.log` next to the server exe in the server folder |
| The person's own game closed when the server started | something stopped processes by name (rule 0.4) |

Before asking in the rVclient Discord, collect: what they did, what they saw, the setup output or
the rV Modes log, and any `crash_trace_*.log`. **Not** `setup-state.json`.

## 6. Removing it

- Private: *Server Status > My private servers > Remove* on the PC that runs it.
- Any server: `Uninstall-RVServer.bat` in the server folder (for example `C:\RVServer`). It asks
  whether to keep the server (stopped) or remove everything; the game is checked and left normal.

---

## Prompt to give your agent

> Read `AI-AGENT-SETUP.md` and `RVServer-Setup\README.txt` in this folder completely before doing
> anything, and follow the ground rules at all times. I want to host a `<private | community>`
> rVclient server on this PC. Check whether this machine is big enough (section 2, including
> Host-Check.ps1), then walk me through the setup one step at a time, explaining each question
> Setup-RVServer.bat asks - I will run it myself. If something fails, read the logs first and tell
> me what they say before suggesting a fix. Ask me before changing any setting, opening any port or
> installing anything. Never share my game files, my setup code or setup-state.json.
