# steampkg

steamcmd wrapper to download and compress games

rec'd usage: `./steampkg.sh -u <username> <appid>`

just check `./steampkg.sh -h` for everything this baby can handle

requires: python3, jq, 7z, unbuffer (from expect package)

todo:

 - add if statement for goldsrc games, ref. linuxgsm [here](https://github.com/GameServerManagers/LinuxGSM/blob/master/lgsm/functions/core_dl.sh)
 - allow selection for language (needs a fat regex)

---

scripts used:

 - vdf2json [https://gist.github.com/ynsta/7221512c583fbfbafe6d]
