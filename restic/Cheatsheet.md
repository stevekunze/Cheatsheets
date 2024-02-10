# general cheatsheet
| command | discription |
| ---- | ---- |
| restic init -r */path/to/repo/* | initialize restic repository on in desired path |
| restic -r */path/to/repo/* backup */path/to/data/that* --compression=max | backup files to repo with max compression | 
| restic -r */path/to/repo* check | check health status of repo | 
| restic -r */path/to/repo* snapshots | list snapshots | 
| restic -r */path/to/repo* ls *snpashot_id* | lists all files of the specified snaphots (use | less or redirect to a file for better readability) |
| restic -r */path/to/repo* mount /path/to/mountpoint | mount your entire repo to a specified location. Only works on Linux |
# personal cheatsheet

These are commands that I use on my personal server and/or clients
Feel free to use them as a reference and modify them to your liking 

| command| discritption|
| --------|------------|
| restic -r /media/steve/Volume/restic-nas-backup/ backup /mnt/truenasshare/ --compression=max --tag created_on_popos | backup entire nas to locally connected usb hdd on my pop os machine.|
| restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max | backup entire nas to hetzner cloud with max compression and .ssh/config and password file for restic-repo authorization|
| restic -r sftp://u1234-sub1@1234.your-storagebox.de:/Restic-Backup-Nextcloud --verbose --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max | backup entire nas to hetzner cloud with max compression and manuel specification of user and target . Using password file for restic-repo authorization 
| restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file forget --keep-daily 14 --keep-weekly 4 --keep-monthly 6  --keep-yearly 1 --prune | apply prune rule to hetzner restic repo and use the specified password file | 
| restic -r /media/steve/Volume/restic-nas-backup/ backup /mnt/truenasshare/ --compression=max --tag created_on_popos
# Aliases 
| Name | Command | host |
| ---- | ---- | ---- |
| backup | alias backup='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file backup /mnt/truenasshare/ --compression=max' | restic.local
| backup_health_check | alias backup_health_check='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file check --read-data' | restic.local
| backup_fast_check | alias backup_fast_check='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file check' | restic.local 
| backup_snapshots | alias backup_snapshots='restic -r sftp:hsb:Restic-Backup-Nextcloud --password-file /home/admin/.restic-hetzner-file snapshots' | restic.local 
| nastohdd-pop | restic -r /media/steve/Volume/restic-nas-backup/ backup /mnt/truenasshare/ --compression=max --tag created_on_popos | pop os client | 
