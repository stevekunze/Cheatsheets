# general cheatsheet
| command | discription |
| ---- | ---- |
| restic -r */path/to/repo/* backup */path/to/data/that* --compression=max | backup files to repo with max compression | 
| restic -r */path/to/repo* check | check health status of repo | 
| restic -r /path/to/repo snapshots | list snapshots | 
| restic -r /path/to/repo ls snpashot_id | lists all files of the specified snaphots (use | less or redirect to a file for better readability)



# personal cheatsheet

These are commands that I use on my personal server and/or clients
Feel free to use them as a reference and modify them to your liking 

| command| discritption|
| --------|------------|
| restic -r /media/steve/Volume/restic-nas-backup/ backup /mnt/truenasshare/ --compression=max --tag created_on_popos | backup entire nas to locally connected usb hdd on my pop os machine.|
| restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max | backup entire nas to hetzner cloud with max compression and .ssh/config and password file for restic-repo authorization|
| restic -r sftp://u1234-sub1@1234.your-storagebox.de:/Restic-Backup-Nextcloud --verbose --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max | backup entire nas to hetzner cloud with max compression and manuel specification of user and target . Using password file for restic-repo authorization |
restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file forget --keep-daily 14 --keep-weekly 4 --keep-monthly 6  --keep-yearly 1 --prune | apply prune rule to hetzner restic repo and use the specified password file |
# Aliases 
| Name | Command 
| ---- | ---- | 
| backup | alias backup='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max' |
| backup_health_check | alias backup_health_check='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file check --read-data' |
| backup_fast_check | alias backup_fast_check='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file check' |
| backup_snapshots | alias backup_snapshots='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file snapshots' |
