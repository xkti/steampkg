# steampkg
- steampkg is a wrapper script for SteamCMD that downloads and packages games for easy archival.
- Run `./steampkg.sh -h` for full usage options.
- Requirements: python3, jq, 7z, unbuffer (expect package)
- If steamcmd.sh is NOT detected, then it will download it automatically.
- [asciinema demo](https://asciinema.org/a/546526)

## Account management

Due to (not-so) recent changes to Steam's authentication process, config.vdf files obtained from the desktop version of Steam will no longer work. **Please login via SteamCMD and use its config.vdf file instead.**

Unlike other tools, steampkg utilises *cached credentials* obtained from Steam's config.vdf file. Only three keys are actually required, however: Accounts, MTBF, ConnectCache. These values would then be made into a new file, `accounts/<your username>.vdf`, located in the same directory as the script.

Example account config (could be either tab or space-separated):

```
"InstallConfigStore"
{
  "Software"
  {
    "Valve"
    {
      "Steam"
      {
        "Accounts"
        {
          "username"
          {
            "SteamID"    "xxxxx"
          }
        }
        "MTBF"    "xxxxx"
        "ConnectCache"
        {
          "CRC32 hash of username with 1 added AFTER (username = f85e06771)"    "verylonghash, ~1000 characters"
        }
      }
    }
  }
}
```

```
$ ls accounts
username.vdf username2.vdf username3.vdf

$ ./steampkg.sh -u username 4000   #Downloads Garry's Mod (assuming username owns it) for Windows
```


---

todo:

 - ~~add if statement for goldsrc games, ref. linuxgsm [here](https://github.com/GameServerManagers/LinuxGSM/blob/master/lgsm/functions/core_dl.sh)~~ unsure, might delete

scripts used:

 - vdf2json [https://gist.github.com/ynsta/7221512c583fbfbafe6d]
