### Week 4: Linux-SysAdmin-Fundamentals

| file system       |           description              |
|:--------------|:---------------------------------- |
|/ (root)        | The root directory that contains every other directory.
|/home           | Contains users’ private file. |
|/etc            | Contains configs, defining how a machine runs and its usage|
|/etc/pwd        | older versions have it, to store pwd |
|/bin, /sbin     | Contain main binary/program files. |
|                | sbin - system executables |
|/var            | Contains files that change over time. |
|/var/logs       | file/system changes overtime. |
|/tmp            | Contains files that are only needed for a short period of time. |
|                | Erase all files when reboot |
|                | CAUTION: a malicious code can be downloaded here |
                
| command       |    Sample      |       description         |
|:--------------|:---------------|---------------------------|
| top           | top | List processes real time, updates every 3 sec  |
|               | top -u jack | list all processes, running by jack |
|               | | Press P: sort according to CPU utilization. |
|               | | Press M: sort by memory usage. |
|               | | Press T: sort by Time column. |
|               | | Press N: sort by PID number. |
| ps            | ps  | snapshot of all processes, args allow diff subset of processes |
|               | ps -axu  | all effective users |
|               |  ps -ef | every process, using standard syntax |
|               | ps -ef \| grep stess | get all the processes that have stress |
|               | ps -axu --sort pmem \| head | process uses the most memory |
|               | ps -u jack | all running processes for jack |
|               | top -u jack | OR |
| kill          |  kill <pid> | to stop process, finishes process before it shuts it down.  |
| killall |  sudo killall stress-ng  | kill all process having stress |
|         | sudo killall -u jack | kill all processes, running by jack |
| apt install   | sudo apt install <package name>  |  |
| =============== | =============== | ============================== |
| john          | sudo john <file with pwd hash>  |  |
| su            | sudo su  | Switches to another user, in this case the root user. |
| sudo          | sudo <cmd>  | Invokes the root user for one command only. |
|               | sudo -l | Lists the sudo privileges for a user. |
|               | sudo -lU adam | List all privileges of adam     |
| whoami        | whoami  | Determines the current user |
| id            | id  | more details(uid, gid, list of groups user is added to gid(groupname)  |
|               |    |uid=1000(sysadmin) gid=1000(sysadmin) groups=1000(sysadmin),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),1003(docker) |
| visudo        |   | Edits the sudoers file. equivalent to nano /etc/sudoer |
| /etc/passwd   |   | List of all users |
|               | cat /etc/passwd \| grep sally  |  Get sally info from passwd |
| =============== | =============== | ============================== |
| usermod       |  | Modify user |
| passwd        | sudo passwd --status mike | check mike status |
| usermod       | sudo usermod -L mike | Lock mike account |
| gpasswd       | sudo gpasswd -d mike general | Remove the user mike from the general group. |
| groups        | groups mike  | Get group info for the user mike. |
| deluser       | sudo deluser --remove-home mike  | Delete the user mike |
|               | cat /etc/group \| grep general | verify group |
| delgroup      | sudo delgroup general | Delete the general group. |
| adduser       | sudo adduser joseph  | Create the user joseph.  |
| addgroup      | sudo addgroup developer | Create a developer group. |
|               | sudo usermod -aG developer joseph  | Add the user joseph to the developer group |
|               | groups joseph  | Verify joseph is added to developer group |
| chmod         |   |  |
| chown         |   |  |
=========================================================================

#### ps sorting
```
Column    Ascending Descending
Heading   Sort      Sort       Alternatives
===============================================
USER      user      -user
PID       pid       -pid
%CPU      pcpu      -pcpu      %cpu and -%cpu
%MEM      pmem      -pmem      %pmem and -%pmem
VSZ       vsz       -vsz
RSS       rss       -rss
TTY       tty       -tty
STAT      stat      -stat
START     start     -start
TIME      time      -time
COMMAND   comm      -comm
```

=========================================================================

