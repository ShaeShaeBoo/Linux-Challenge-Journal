# Linux-Challenge-Journal
# My Linux Upskill Challenge Journal
BITA Kernel Crew · Cohort 1 · Sept 2026
## Day 0
- Set up my server (DigitalOcean / Killercoda) — it's alive 🐧
- ssh root@167.71.18.230 on MacOs
- ## Day 1
- commands to use:
  whoami:name of server (root)
  sudo apt update:update server
  uptime-how long server been running
  uname -r:kernel version
  lscpu:CPU
  lsblk:block storage
  free -h:human readable files
  tree /home/:structural
  netstat -i:network connection
  ip addr:ip address 
- ## Day 2
    pwd:printing working directorty
    cd:change directory
    cd /bin
    
- ## Problems I hit and how I fixed them:

**Unable to connect to SSH on Mac**
  Issue: When connecting to SSH server, timed out. Was able to launch cloud ssh on DigitalOcean 
 
 Troubleshoot:
  checked UFW from DO (sudo ufw status) status active
  22/tcp wasn't active; to enable 22 (sudo ufw allow 22/tcp)
  Rule added
  verify rule: sudo ufw status
  22/tcp    ALLOW    Anywhere
80/tcp    ALLOW    Anywhere
22/tcp (v6)  ALLOW    Anywhere (v6)
80/tcp (v6)  ALLOW    Anywhere (v6)
connected to 22 successfully; now connection to 167.71.18.230 closed
run nc -vz 167.71.18.230 22 on DO
after running ssh shaeshaeboo@167.71.18.230, permission denied (publickey)
run ls -la ~/.ssh on Mac
public key id_ed25519, if key exist run cat ~/.ssh/id_ed25519.pub
key started with ssh-ed25519 AAAA....
on DO run
mkdir -p ~/.ssh
chmod 700 ~/.ssh
edit nano ~/.ssh/authorized_keys
paste Mac public key (include your_email@example.com) into line and save with
Ctrl + O
Enter
Ctrl + X
run chmod 600 ~/.ssh/authorized_keys
Try SSH again on Mac
ssh -i ~/.ssh/id_ed25519 shaeshaeboo@167.71.18.230
