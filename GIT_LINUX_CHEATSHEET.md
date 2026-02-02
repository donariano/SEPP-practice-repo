# 🚀 Git & Linux Cheat Sheet

A compact reference for common Git and Linux commands. Use this as a quick reminder for everyday tasks. ✅

---

## 🔧 Git — Basics & Workflow

- **Configure**
  - `git config --global user.name "Name"`
  - `git config --global user.email "you@example.com"`

- **Start / Clone**
  - `git init` — initialize repo
  - `git clone <repo>` — clone remote

- **Staging & Commit**
  - `git status` — view state
  - `git add <file>` / `git add .` — stage changes
  - `git commit -m "message"` — commit staged changes
  - `git commit -am "message"` — add modified tracked files + commit

- **Amend & Fix**
  - `git commit --amend` — edit last commit
  - `git restore <file>` — discard unstaged changes
  - `git restore --staged <file>` — unstage file

- **Branches**
  - `git branch` — list branches
  - `git branch <name>` — create branch
  - `git switch <name>` or `git checkout <name>` — switch branch
  - `git branch -d <name>` — delete branch

- **Merging & Rebasing**
  - `git merge <branch>` — merge into current
  - `git rebase <branch>` — reapply commits on top of branch
  - `git rebase -i <commit>` — interactive rebase

- **Stash**
  - `git stash` — save working state
  - `git stash list` / `git stash pop` / `git stash apply`

- **Remote**
  - `git remote -v` — list remotes
  - `git fetch` — fetch from remote
  - `git pull` — fetch + merge (or `git pull --rebase`)
  - `git push` — push branch

- **Tags**
  - `git tag <name>` — create tag
  - `git push origin <tag>` — push tag

- **Inspecting history**
  - `git log --oneline --graph --decorate` — compact visual log
  - `git diff` — show changes
  - `git show <commit>` — details for a commit

- **Undoing / Reset**
  - `git reset --soft <commit>` — move HEAD, keep changes staged
  - `git reset --mixed <commit>` — move HEAD, keep changes unstaged (default)
  - `git reset --hard <commit>` — move HEAD and discard working tree
  - `git revert <commit>` — create commit that undoes a commit (safe for public history)

- **Find & Debug**
  - `git blame <file>` — show who changed each line
  - `git bisect start` / `git bisect bad` / `git bisect good` — find bad commit

- **Helpful Tips**
  - `git cherry-pick <commit>` — apply single commit onto current branch
  - `git reflog` — recover lost commits
  - `git remote add origin <url>` — set remote
  - `git checkout -b <branch>` — create + switch

---

## 🐧 Linux — Common Commands

### Files & Navigation
- `pwd` — print working directory
- `ls -la` — list all (long format)
- `cd <dir>` — change directory
- `mkdir -p <dir>` — create directory (parents)
- `touch <file>` — create empty file / update timestamp
- `cp -r src dst` — copy recursively
- `mv src dst` — move/rename
- `rm file` / `rm -rf dir` — remove file/dir (be careful!)
- `ln -s target linkname` — create symbolic link

### Viewing Files
- `cat file`
- `tac file` — reverse print
- `less file` — paging
- `head -n 20 file` / `tail -n 20 file` — start / end
- `tail -f file` — follow file updates

### Text Processing
- `grep -R "pattern" .` — recursive search
- `egrep "pattern1|pattern2" file` — extended regex
- `sed 's/old/new/g' file` — stream edit
- `awk '{print $1}' file` — field processing
- `sort` / `uniq -c` / `cut -d' ' -f1` — common pipeline tools
- `xargs` — build and run commands from stdin

### Permissions & Ownership
- `chmod 755 file` — change permissions
- `chown user:group file` — change owner
- `umask` — default file creation permissions

### Processes & Jobs
- `ps aux | grep process` — show processes
- `top` / `htop` — interactive process viewer
- `kill PID` / `kill -9 PID` — terminate process
- `pkill -f name` — kill by name
- `&` — run background
- `jobs` / `bg` / `fg` — job control
- `nice -n 10 command` / `renice` — adjust priority

### Networking & Remote
- `ip a` or `ifconfig` — network interfaces
- `ss -tuln` / `netstat -tuln` — open ports
- `ping host` / `traceroute host`
- `curl -fsSL http://...` — fetch URL (useful in scripts)
- `wget <url>` — download
- `ssh user@host` — remote shell
- `scp src dest` — copy files over SSH
- `rsync -avz src dst` — synced copy

### Disk & Storage
- `df -h` — disk usage by filesystem
- `du -sh dir` — directory size
- `mount` / `umount` — mount/umount filesystems

### Searching Files
- `find /path -name "*.log" -mtime -7` — find files
- `locate file` — fast search using mlocate DB

### Compression / Archives
- `tar czf archive.tar.gz dir` — create gzipped tar
- `tar xzf archive.tar.gz` — extract gz
- `zip -r archive.zip dir` / `unzip file.zip`
- `gzip` / `gunzip` / `bzip2` / `xz` — compression tools

### Package Management (Debian/Ubuntu)
- `sudo apt update` — refresh packages
- `sudo apt install <pkg>` — install
- `sudo apt remove <pkg>` — remove
- `sudo apt upgrade` — upgrade packages

### Systemd & Logs
- `systemctl status <service>` / `systemctl start/stop/restart <service>`
- `journalctl -u <service>` — logs for a service
- `journalctl -f` — follow system journal

### Users & Access
- `sudo <cmd>` — run as root
- `adduser <user>` / `userdel <user>`
- `passwd <user>` — change password
- `groups <user>` — list group memberships

### Scheduling
- `crontab -e` — edit crontab for current user
- `watch -n 1 <cmd>` — run command every N seconds

### Shell & Environment
- `export VAR=value` — set env var for session
- `echo $VAR` — print env var
- `alias ll='ls -la'` — create alias
- `history` / `!n` / `!!` — reuse history

---

## ⚡ Quick Examples & Tips

- Git: create feature branch, commit, push
```bash
git checkout -b feature-x
# work...
git add .
git commit -m "feat: add x"
git push -u origin feature-x
```

- Restore file from previous commit
```bash
git checkout HEAD~1 -- path/to/file
```

- Find large files in repo (Linux)
```bash
find . -type f -exec du -h {} + | sort -hr | head
```

- Recursively replace text in files (careful!)
```bash
grep -Rl "OLD" src/ | xargs sed -i 's/OLD/NEW/g'
```

---

> Note: This sheet focuses on practical, safe commands. For destructive ops like `rm -rf` and `git reset --hard`, double-check your target and consider backups. ⚠️

---

Happy hacking! ✨
