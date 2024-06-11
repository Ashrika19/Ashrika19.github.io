**PROCESS**
- In a linux process is any active (running) instance of a program 
- whenever a command is issued in linux,it creates/starts a new process
- FOR EXAMPLE
- pwd when issued is used to list the cureent directory location the user is in ,a process starts
- every process it starts it will end also
- every process has an resource like CPU RAM HDD

**PROCESS DIVIDED INTO 2 TYPES**
- **Managing linux process**
- **Monitoring linux process**

**ID**
- It means to say identity of person
- PID - process ID
- PPID - parent process id

**TO monitor the process**
- #top

**KILL PROCESS**
- There are 64 types to kill the process
- sigkill = -9  (forcefully kill)
- sigterm = -15 (terminating kill)
 
**To get the process id**
- #pidof firefox
- #kill -9 3789

**To see the process**
- #ps
- #ps aux
- #jobs
- #fg %2
- #bg %2
- #lscpu (to get info abt cpu)

**CONTROLLING SERVICES AND DAEMONS**
- **DAEMONS** - daemons that are running in background. Daemon services are those which start at the time of system start and end when system stops

- #systemctl status httpd
- #systemctl start httpd (to start the service)
- #systemctl stop httpd (to stop the service)
- #systemctl enable --now httpd (to start and enable service)
- #systemctl disable --now httpd

**SYSTEMD IS THE FIRST PROCESS WHOSE PID IS 1**

**CONFIGURING AND SECURING SSH**
 
 - We have 2 types of Authentication
 - key based authentication
 - command to generate key
 - # ssh-keygen
 - # cd .ssh
 - # ssh-copy-id root@servera
 - # ssh root@servera

 - password base authentication

**TO SEE THE IP ADDRESS**
- #ifconfig
       or 
- #ip a s

**TAR**
- TAR stands for Tape Archive
- TAR is a command in linux used for creating,viewing and extracting files.
- It bundles file into a single archive file.
- we can use linux tar command to create compressed or uncompressed archive files
  
  - -z   --gzip   use gzip compression(.tar.gz)
  - -j   --bzip2  use bzip2 compression(.tar.bz2)

  **HOW TO CREATE A TAR**
  - #mkdir myetcbackup
  - #tar -jcf /root/myetcbackup.tar.bz2 /etc  (to create the tar file)
  - #tar -xjf /root/myetcbackup.tar.bz2 (to extract the tar file )
   
   **SCP(SECURILY COPY)**
  **to copy file from controller to node1**
  - #scp /etc/yum.conf root@node1:/root

  **to get a file from node1 to controller**
  - #scp root@node1:/etc/hosts /root

  **Rsync**
  - rsync is a file transfer utility designed to move data from one linux network host to another 

  - rsync -av root@node1:/var/log serverlogs

  