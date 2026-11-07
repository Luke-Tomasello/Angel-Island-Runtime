# Angel Island Runtime

The **Angel Island** Ultima Online server, built and ready to run: download it, start it, and connect. It's the same
server as the **[Angel Island Server](https://github.com/Luke-Tomasello/Angel-Island-Server)** source repository,
built from scratch from it: each update here is tagged `svn-r<number>`, and the source tag with the same name is exactly
what it was built from.

## What you need

- **Windows** and the **[.NET 8 Runtime](https://dotnet.microsoft.com/download/dotnet/8.0)** (to build the server
  yourself, use the source repository and the .NET 8 SDK instead).
- **Ultima Online client files.** The server finds them through the registry, or asks for the folder the first time.
  Players connect with client **6.0.1.10**; other versions get a warning.

## Run

Every shard is the same program, started with a flag. With no flag, it asks which one to run.

| Flag | Shard | Port |
|---|---|---|
| `-uols` | Login server: players connect here and pick a shard | 2593 |
| `-uoai` | Angel Island | 3593 |
| `-uosp` | Siege Perilous (`-Siege1`, `-Siege2` for its variants) | 3594 |
| `-uomo` | Mortalis | 3595 |
| `-uose` | Seasons (`-Season1`, `-Season2`, ... for a season) | 3596 |
| `-uoup` | Upheaval | 3597 |
| `-uotc` | Test Center: add to a shard's flag to run it as its test center | 3602 |
| `-uoev` | Event shard: add to a shard's flag to run it as an event shard | 3601 |

The ports are in `Ports.json`. Other flags you may want:

| Flag | What it does |
|---|---|
| `-usedb` | Share accounts and passwords between servers (a common SQLite database) |
| `-nopatch` | Skip the startup patcher (one-time patches for existing worlds) |

```
"GMN Core.exe" -uols -usedb          the login server
"GMN Core.exe" -uoai -usedb          Angel Island
"GMN Core.exe" -uosp -uotc -usedb    Siege Perilous Test Center
```

To try one shard, start it and connect your client to its port. To run several, copy this folder once for each (for
example `ShardAI`, `ShardSP`, `ShardLS`), start the login server and the shards, and connect your client to the login
server on port 2593.

## The first start

- With no world yet, the server starts a new one: it creates `Saves\` and `Logs\` beside `GMN Core.exe`, runs its
  one-time patches, and spawns the world. Messages about things a patch expected in an older world are normal on a new
  one.
- It offers to create the first account. That account is **Owner**, one level above Administrator.
- Windows asks whether to let `GMN Core.exe` through the firewall: allow it, or players can't connect.

## World files

To start from our worlds instead of a new one, copy a world repository's `Saves` folder here (beside `GMN Core.exe`)
before the first start. The server brings an older save up to date as it loads it.

- [Angel Island World Files](https://github.com/Luke-Tomasello/Angel-Island-World-files): Angel Island as of July 2024,
  a customized OSI Publish 15 spawn.
- [Siege Perilous World Files](https://github.com/Luke-Tomasello/Siege-Perilous-World-Files): Siege Perilous as of July
  2024, a faithful OSI Publish 13.6 spawn.

Both include the Custom Housing Preview area (any of our 56 custom houses, to see and buy), every township, and the
music library: about a hundred songs players composed with the music system.

## Optional settings

The server runs without any of these; each turns on a feature. They are Windows environment variables.

| Variables | For |
|---|---|
| `AI.NOREPLY.ADDRESS`, `AI.NOREPLY.PASSWORD`, `AI.EMAIL.HOST`, `AI.EMAIL.HOST.PORT`, `AI.EMAIL.USER`, `AI.EMAIL.ACCOUNTING`, `AI.EMAIL.ANNOUNCEMENTS`, `AI.EMAIL.DEVNOTIFY`, `AI.EMAIL.DISTLIST.PASSWORD`, `AI.EMAIL.SHARDOWNER` | Email: account notices, announcements, crash reports |
| `AI.MMAccountId`, `AI.MMlicenseKey` | GeoIP lookups with your own MaxMind account |
| `AI.LOGINDB`, `AI.IPEXCEPTIONDB`, `AI.FIREWALLDB` | Where the shared databases live (`-usedb`) |
| `AI.BuildInfoDir` | Where the build number file, `Core 6.info`, is kept (here, by default) |

## The build number

`Core 6.info` holds the build number the server reports at startup (`Version 6.1.xxxx, Build n`). This runtime counts its
own builds, one per update, starting from 1: it isn't Angel Island's live build number, and a server you build yourself
counts its own.

## Related

- [Angel Island Server](https://github.com/Luke-Tomasello/Angel-Island-Server): the source
- [Angel Island Music System](https://github.com/Luke-Tomasello/Angel-Island-Music-System): the music system, as a
  drop-in for RunUO servers
- [ClassicUO, Angel Island version](https://github.com/Luke-Tomasello/ClassicUO-Angel-Island-Version),
  [RazorCE, Angel Island version](https://github.com/Luke-Tomasello/RazorCE-Angel-Island-Version) and the
  [Common Shard Launcher](https://github.com/Luke-Tomasello/Common-Shard-Launcher): the clients the server checks for an
  approved configuration
- [Client map and music files](https://github.com/Luke-Tomasello/client-server-map-and-music-files)
- YouTube: [Ultima Online Free Shard](https://www.youtube.com/@UltimaOnlineFreeShard); getting started:
  [part 1](https://youtu.be/0kauX-W5BLI), [part 2](https://youtu.be/8zNv5ryd6_U)
- Discord: [discord.gg/GXcR2DsSnb](https://discord.gg/GXcR2DsSnb)

## License

GPL (see `LICENSE`). The source is the Angel Island Server repository, at the tag with this update's name. Angel Island
is built on RunUO, by the RunUO Software Team, and on twenty years of work by Angel Island's developers, staff and
players.
