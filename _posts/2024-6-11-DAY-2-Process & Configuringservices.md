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
