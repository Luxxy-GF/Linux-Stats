# linux-stats
This script hosts a express website on port 999 with all the daemon of the node, Using the (linux-stats) bot, it will grab this data from the node and store it locally on the bot. 

## Getting Started
These instructions will get the script up and running 

### Clone the repo, (Here we clone it to the root folder. You can change this but make sure to update the WorkingDirectory, PIDFile, and ExecStart in `Running the script`)
```
git clone https://github.com/Luxxy-GF/linux-stats.git 
```

### Installing requirements 
```
npm i
```
This will install all needed packages

### Setting up config.json
Copy example-config.json or rename it. 
Edit the file and set externalPassword to something that both the bot and the script has (MUST BE THE SAME)

### Running the script
We run this as a service so that it boots on startup and is always running when the server is online. 
To do this follow these steps: 
Run: `nano /etc/systemd/system/floppa.service` and enter the following:
```
[Unit]
Description=Floppa Stats Daemon

[Service]
User=root
#Group=some_group
WorkingDirectory=/root/linux-stats
LimitNOFILE=4096
PIDFile=/root/linux-stats/daemon.pid
ExecStart=/usr/bin/node /root/linux-stats/index.js
Restart=always

[Install]
WantedBy=multi-user.target
```
Run `systemctl enable --now floppa` this will start the script, you can view its status using `systemctl status floppa`
