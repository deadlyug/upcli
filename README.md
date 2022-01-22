# Upcli
Script to automate backup mysql database and backup a spesific directory.

## Depedency 
- cronie
- shc
- jq

## Install
```
curl -s https://raw.githubusercontent.com/deadlyug/upcli/v0.1-beta/install | bash
```
To check upcli is installed, make sure this command to show version of upcli.
```
upcli -v
```

## Usage
You can create backup scheduller by running this command, then fill up all value needed by **upcli**.
```
upcli
```
If your console doesn't support input feedback you need to fill the value using option like this.
```
upcli -n <backup-name> \
  --db-username <your-mysql-username> \
  --db-password <your-mysql-pass> \
  --db-name <your-mysql-database-name> \
  --path-dir /path/to/a/directory/ \
  --telegram-token <your-telegram-token \
  --telegram-chatid <your-telegram-chatid> \
  --nextcloud-username <your-nextcloud-username> \
  --nextcloud-password "<your-nextcloud-password>" \
  --nextcloud-path-db path/to/nextcloud/backup/database \
  --nextcloud-path-dir path/to/nextcloud/backup/directory \
  --retention-daily 7 \
  -q
```
option `-q` is for quiet mode.
<br><br>
If you want to backup only database, you do it like this.
```
upcli -n <backup-name> \
  --only-db \
  --db-username <your-mysql-username> \
  --db-password <your-mysql-pass> \
  --db-name <your-mysql-database-name> \
  --telegram-token <your-telegram-token \
  --telegram-chatid <your-telegram-chatid> \
  --nextcloud-username "<your-nextcloud-username>" \
  --nextcloud-password <your-nextcloud-password> \
  --nextcloud-path-db path/to/nextcloud/backup/database \
  --retention-daily 7 \
  -q
```
and if you want to backup only a directory you have to spesify option `--only-dir`
<br><br>
if you want to see all the option, do this command.
```
upcli -h
```
#### Usage with config file
First you have to copy config template, if you installed upcli using root user, the config templete placed in this directory `/etc/upcli`.
```
cp /etc/upcli/config.template /path/to/your/prefered/directory
```
if you installed upcli using reguler user, the config template placed in this directory `/home/user/.config/upcli`.
```
cp ~/.config/upcli/config.template /path/to/your/prefered/directory
```
edit the config file as you liking. <br>
and then run this command to create backup scheduller using your config file.
```
upcli -f <path/to/your/config-file>
```
:information_source: if you want to create another backup scheduller you need to copy the config again, because **upcli** delete your config file for security reason.
#### List backups
```
upcli -l
```
#### Disable a backup
```
upcli -d <backup-name>
```
#### Delete a backup
```
upcli -D <backup-name>
```

## Uninstall
```
curl -s https://raw.githubusercontent.com/deadlyug/upcli/v0.1-beta/uninstall | bash
```

## Copyright
Copyright belongs to Allah
