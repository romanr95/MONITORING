# Easy Telegram monitoring and notification with Uptime Kuma
## installation 
### Updating repositories
```bash
sudo apt update && sudo apt upgrade -y
```
### Set up git
```bash
sudo apt install git 
```

### Set up Nodejs and NPM
```bash
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash - && \
sudo apt-get install nodejs -y && \
echo -e "\nnodejs > $(node --version).\nnpm  >>> v$(npm --version).\n"
```

### Set up Uptime Kuma
   
```bash
cd $HOME
git clone https://github.com/louislam/uptime-kuma.git
cd uptime-kuma
npm run setup
```
### Set up PM2 if you haven"t got it:

```bash
cd $HOME
sudo npm install pm2 -g && sudo pm2 install pm2-logrotate
```
### Launch server
```bash
cd $HOME/uptime-kuma
sudo pm2 start server/server.js --name uptime-kuma
```
### Follow the link http://localhost:3001 after launching.

```bash
http://Your_Server_IP:3001
```
## Install monitoring 
At the beginning add a new monitor 

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(1).png" width="400" alt="" />

Monitor type, select "TCP port"

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(2).png" width="400" alt="" />

As “Hostname” write IP address of your server and as a “Port”, port to which your node listens. Standard is 26656

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(6).png" width="400" alt="" />

If everything do well it should resemble this: 

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(3).png" width="400" alt="" />

## Install telegram alerts 


Go to “settings” and choose “notification” 

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(4).png" width="400" alt="" />

select “Setup Notification” After you need to get a Bot token and Chat ID(or your user ID) Follow instructions under to do so:


| KEY | VALUE |
|---------------|-------------|
| Chat ID | Your user id you can get from [@userinfobot](https://t.me/userinfobot). The bot will only answer to messages sent from the user. All other messages are dropped and registered on the bot's console |
| Bot token  | Your telegram bot access token you can get from [@botfather](https://telegram.me/botfather). To generate new token just follow a few simple steps described [here](https://core.telegram.org/bots#6-botfather) |

Write over your Chat ID and Bot token and don’t forget to switch on “Apply on all existing monitors” 

<img src="https://github.com/romanr95/MONITORING/blob/main/uptimekuma_1%20(5).png" width="400" alt="" />

After it’s finished, your bot should inform you if your nod is down.
Good luck! 

### Official documentation:

https://github.com/louislam/uptime-kuma
