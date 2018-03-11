# 1. Setup

How to do our jobs efficiently and reproducibly

### 0\) Get a Laptop or Desktop

---

[mac 使用技巧](https://www.evernote.com/l/ABIaUQq5Y4ZPv53w8iYevcDzHmCNY3AfIhU)

### 1\) Get a Linux OS

---

#### 1a\) docker or VM

[https://docs.docker.com/docker-for-mac/install/](https://docs.docker.com/docker-for-mac/install/)

#### 1b\) ssh & login

.bashrc

### 2\) Learn an Editor

---

#### A. **Vim** -- [Learn Vim Progressively](http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/)

> Learn [vim](http://www.vim.org/) and it will be your last text editor. There isn’t any better text editor that I know of. It is hard to learn, but incredible to use.I suggest you teach yourself Vim in 4 steps:
>
> 1. **Survive**
> 2. Feel comfortable
> 3. Feel Better, Stronger, Faster
> 4. Use superpowers of vim

#### B. **Atom -- **[Tutorial and Tips ](https://www.evernote.com/l/ABJeb9FdBc1BC6AZSgWh4Ujc_StdcFYl-kw)

> A hackable text editor for the 21st century

### 3\) README

---

Document your project using markdown language \(available in wiki, gitbook, github, etc\)

### 4\)  backup & contab

---

> [Tips on 备份数据、保存中间数据 \| 数据安全](https://www.evernote.com/l/ABLaXPPQIg1FM5Kgl1AoLqLj67CR1Cv44ws)

**It's necessary to copy data regularly: **

\(1\) Prepare a backup script, for example, "_~/backup.sh_"

```bash
#!/bin/bash

RSYNC="rsync --stats  --compress --recursive --times --perms --links --delete --max-size=100M --exclude-from=/home/zl222/.rsync/exclude"

#1. Local backup  
#backing up /home1/zl222 to /home/zl222/sub_dir

echo "1. Backup of /home1/zl222 start at:"
date

$RSYNC /home1/zl222/ /home/zl222/backup_ncrna_home1/ 

echo "Backup end at:"
date



#2. Remote backup 

RSYNC="rsync --stats  --compress --recursive --times --perms --links --delete --max-size=100M --files-from=/home/backup1/backup_file"

echo "2. Backup 172.22.220.20:/data/ to /home/backup1/ start at:"
date

$RSYNC liushanhu@172.22.220.20:/data/ /home/backup1/

echo "Backup end at:"
date
```

\(2\) Using "crontab" command to execute the backup script routinely, and record in a log file, for example,

execute the command "_~/backup.sh &gt; ~/backup.log_" in 5:10am everyday:

```
1) open crontab and edit it by the following command: 

crontab -e 

2) type in the following lines: 

# minute hour day_in_month month day_in_week command
     10   5  * * *   ~/backup.sh > ~/backup.log 

3) exit and save (like in VIM)
```


