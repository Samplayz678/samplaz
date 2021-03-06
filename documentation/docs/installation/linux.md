# Installation on a Linux server

## Prerequisites

- [Discord Application](#create-a-discord-application)
- [NodeJS & NPM](#install-nodejs-npm)

### Create a Discord Application

- go to the [Discord Developer portal](https://discord.com/developers/applications)
- create a new application + bot
- create a bot invitelink using it's client id [here](https://discordapi.com/permissions.html)
- save the bot token for later

### Install nodejs & npm

follow [those](https://github.com/nodesource/distributions) instructions

## Installation

- [Configuration](#configuration)
- [Lavalink](#lavalink)
- [Final Steps](#final-steps)

### Configuration

- run `git clone https://github.com/SudhanPlayz/Discord-MusicBot.git`
- go into the folder with `cd Discord-MusicBot`
- edit the botconfig.js with the tokens from earlier

### lavalink

use

```
host: "lava.link",
port: 80,
pass: "youshallnotpass"
```

or [host your own](https://github.com/freyacodes/Lavalink)

### Final steps

- run `npm install`
- start the bot with `node index.js`

### Dashboard setup.

> You can do this in 2 ways, with a custom domain or with your vps/server ip.

### Dashboard with custom domain

##### With Nginx

Create a new file in `/etc/nginx/sites-available`

> you can use whatever your favorite text editor, but I'll be using vim cause I'm used to it

Do `vi /etc/nginx/sites-available/musicbot.conf`
Then enter this example config

```c
server {
    listen 80;
    server_name example.co,;

    location / {
        proxy_set_header   X-Forwarded-For $remote_addr;
        proxy_set_header   Host $http_host;
        proxy_pass         http://127.0.0.1:3000;
    }
}
```

> Replace `example.com` with your domain

##### [not done] With Apache

#### Dashboard with IP

- open port 80, Then edit the `botconfig.js` and change the `Port` on line `5`, change it to 80, `Website` line `18` to `https://192.yourserverip.0.0`

![BangExample](https://i.imgur.com/4t4Zm2a.png)

- Go to the Discord Developer Portal under the OAuth2 tab. Then put your server ip in this format `http://yourip.yes.number.only/api/callback`

![Example](https://i.imgur.com/JmxmdM0.png)
