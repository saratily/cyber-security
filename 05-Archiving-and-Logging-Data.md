### Week 5: Archiving-and-Logging-Data

3 kinds of backups
1. Full backup
2. Incremental backup
3. Differential backup


grep -R "Megan,Patel" epscript/

| command       |    Sample      |       description         |
|---------------|:---------------|---------------------------|
| tar | tar [options] [archive_name] [objects to archive] | 
| compress/archive | $ tar cvvWf 20230410-epscript.tar epscript/ > 20230410-epscript.txt |  cmd to compress / archive a dir or file |
|   | $ tar cvf archive.tar ./Documents ./Downloads | Create tar of multiple dir |
| | cvvWf                       | compress, very verbose, verify archives after writing, archive filename  |
| | 20230410-epscript.tar       | archive name                    |
| | epscript/                   | dir to be archived              |
| | 20230410-epscript.txt       | save the output of tar cmd      |
||||
| extract |$ tar xvvf 20190814epscript.tar -C patient_search/ epscript/patients | extract epscript/patients insode .tar |
| | $ tar xvf 20190814epscript.tar -C patient_search/ --wildcards "*.csv" | extract csv files only using wildcards |
| | tar                   | command                           |
| | xvvf                  | extract, very verbose, flag for archive filename |
| | 20190814epscript.tar  | tar file we want to extract from  |
| | -C                    |  saves the indicated patient directory and its files |
| | patient_search/       |  dir where we want to extract files (dir should be created before use) |
| | epscript/patients     | extracting files from this dir from archive ONLY. |
||||
| view/verify tar content | tar tvvf epscript_back_sun.tar --incremental \| less | |
| | t -> listing only | |
||||
| Incremental backup | tar cvvWf full.tar --listed-incremental=epscript_backup.snar --level=0 testenvir | level 0 of testenvir dir |
| snar file format  | Y ->  Modified |  Types of record in snapshot files: Y, N & D|
| | D -> Deleted | | 
| | N -> No change | |
| | D indicates directories. | | 
| | Y indicates that these file are contained in the epscript_back_sun.tar archive. | |
||||
| | tar cvvWf inc1.tar --listed-incremental=epscript_backup.snar testenvir | increament # 1 -> backup ONLY the changes made since last backup |
| | tar cvvWf inc2.tar --listed-incremental=epscript_backup.snar testenvir | increament # 2 |
| Extract from incremental backups| tar xvvf full.tar  --increamental | extract full tar |
| | tar xvvf inc1.tar --increamental | extract increament # 1 on top of full |
| | tar xvvf inc2.tar --increamental | extract increament # 2 on top of full & increament # 1 |
||||
| gzip  | gzip archive.tar  | open source - to compress tar -> archive.tar.gz |
||||
| crontab       | MM HH DD MM Day [cmd] | MM -> minutes (0-59)\ HH -> Hour (0-23)\ DD -> Day of month (1-31)\ MM -> month(1-12)\ Day -> Day of Week(0-6, where 0=Sunday)| 
| | 36 2 * * 0 tar -zcf /var/backups/home.tar /home |  |
| Verify cron is running | $ sudo systemctl status cron | |
| Edit cron | $ crantab -e |  |without filters returns entire content of logs, hard to analyze them
| List cron jobs | $ crontab -l | to inspect user crontab  |
| List all cron files | $ sudo ls ./crontabs |
||||
| logs          | /var/logs  |  |
| | sudo systemctl restart systemd-journald | | 
| journalctl    | journalctl [options] [info being filtered]  | without filters returns entire content of logs, hard to analyze them |
| | sudo journalctl | List too much information |
| | sudo journalctl --list-boots | displays lines for individual boots | 
| | sudo journalctl -ef | -e -> display end of journal\ f -> gets updated with activities in terminal 2 |
| logrotate | /etc/logrotate.conf | | 
```sudo nano <service_name> 
/var/log/<service_name> {
	daily / weekly	- period
	rotate <n>	- interval  
	create		- new file while rotate
	notifempty	- donot rotate empty files
	dateext		- use date as a suffix
	compress	- compress backlog
	delaycompress	- except most recent backlog
	missingok - if missing, don't generate error
}
```
| command       |    Sample      |       description         |
|---------------|:---------------|---------------------------|
| auditd        | sudo auditd -l | List all rules  |
```
$ sudo nano /etc/audit/rules.d/audit.rules

-w /etc/shadow -p wa -k shadow
-p -> permission
wa -> write and 
-k -> key
```
=========================================================================




### Week 6
| command       |    Sample      |       description         |
|---------------|:--------------:|--------------------------:|
| ;             |   |  |
| &&            |   |  |
| |             |   |  |
| >             |   |  |
| >>            |   |  |
| alias         |   |  |
| ~/.bashrc     |   |  |
| ~/scripts     |   |  |
| custom cmd    |   |  |
| #             |   |  |
| if            |   |  |
| if/else       |   |  |
| &&            |   |  |
| ||            |   |  |
| List          |   |  |
| for loop      |   |  |
=========================================================================