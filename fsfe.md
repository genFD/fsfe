# Server setup

## Change to home directory
```sh
cd ~
```

## Create a new directory if it doesn't exist

```sh
mkdir -p ~/.ssh
```

## Create authorized_keys file and paste public key

```sh
vi ~/.ssh/authorized_keys
```

## Change file permissions

```sh
chmod 644 ~/.ssh/authorized_keys
```

## Disable root login

```sh
sudo vi /etc/ssh/sshd_config
```

## Restart ssh daemon

```sh
sudo service sshd restart
```

# NGINX

- a web server :
- a reverse proxy :

## Install nginx
```sh
sudo apt install nginx
```

## Start nginx
```sh
sudo service nginx start
```

## Show nginx config
```sh
sudo less /etc/nginx/sites-available/default
```
**Base directory for request**
root/var/www/html
*********************

- add index.php if you're using php 
 **html defaults**
index index.html index.htm index.nginx-debian.html;

server_name _;

**Location block**
location / {
 - first attempt to serve request as file, then
 - as directory, then fall back to displaying a 404.
 **directive**
 try files $uri $uri/ = 404
}

## Create and edit index.html

```sh
sudo vi /var/www/html/index.html
```

# NODE JS

## Install nodejs and npm

```sh
sudo apt install nodejs npm
```

## Install git

```sh
sudo apt install git
```

# APPLICATION ARCHITECHTURE

## Change ownership of the www directory to the current user

```sh
sudo chown -R $USER:$USER /var/www
```

## Create application directory

```sh
mkdir /var/www/app
```

## Move into app directory and intialize empty git repository

```sh
cd /var/www/app && git init 
```

## Create directories

```sh
mkdir -p client/js client/html client/css
```

## Create empty application file

```sh
touch app.js
```

## Initialize project

```sh
npm init 
```

## Install express 

```sh
npm i express --save
```

## Edit app

```sh
vi app.js
```


## Edit Nginx configuration
```sh
sudo vi /etc/nginx/sites-available/default
```

location /{
 proxy_pass http://127.0.0.1:3000/;
}



# PROCESS MANAGER

- Keeps your application up and running
- Handles errors and restarts
- Handles logging and clustering

## Install PM2

```sh
sudo npm i -g pm2
```

## Start PM2

```sh
pm2 start app.js
```

## Setup auto restart

```sh
pm2 startup
```

# VERSION CONTROL

- Create GIT repository
- Add ssh to github

```sh
cd ~/.ssh
ssh-keygen 
```
 - save
 - copy id_rsa_pub ssh key and add it to github
 - connect remote to server using ssh
  - copy remote repo ssh

  ```sh
  cd /var/www/app/
  git remote add origin git@github.com:hermkan/fsgig.git
  git remote -v
  ````

- Add remote repository
- Push local repository to github

# Recap - How the internet works

- Domain looks up ip address via name server
- Name server returns ip address that passes off to a node and eventually hits a server.
- The server then passes off to a web server (NGINX)
- Which then passes it to an application server, and the application server was Express

# Standard Streams

- The standard way for input to go in and output to go out for almost all Unix Applications/also how errors are handled.

- What we do with the standards is redirection : write from files, read from files

- redirection Operators:
|  
read from stdout
> 
write stdout to file
>> 
append stdout to file
< 
read from stdin
2> 
read from stderr

# Finding things

- Find command (search file names)

```sh
find    /bar        -name  foo.txt
command  directory  option file/folder
```

- grep command (search file content)


# Security
ways to lock down our server:
- SSH
- Firewalls

## Install nmap

```sh
sudo apt install nmap
man nmap
```
## Run nmap

```sh
nmap YOUR_SERVER_IP_ADDRESS
```

## Run nmap with more service

```sh
nmap -sV YOUR_SERVER_IP_ADDRESS
```

## Check firewall status

```sh
sudo ufw status
```

## Start ufw

```sh
sudo ufw enable
```
## Enable ssh http

```sh
sudo ufw allow ssh
sudo ufw allow http
```
## Reject  http

```sh
sudo ufw reject http

```

## Enable firewall

```sh
sudo ufw enable
```

- Keep software up to date

Install unattended upgrades
```sh
sudo apt install unattended-upgrades
```
View conf files
```sh
cat /etc/apt/apt.conf.d/50unattended-upgrades
```
- Use a VPN
# Permissions

# Upgrade node

## Download setup script from nodesource

```sh
curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh
```
## Run script

```sh
sudo bash nodesource_setup.sh
```
## Install nodejs

```sh
sudo apt install nodejs
```

## Update outdated packages

```sh
sudo npm update -g
```

# HTTP

# Edit Nginx configuration

```sh
sudo vi /etc/nginx/sites-available/default
```

# CONTAINERS

## Display running processes

```sh
top
```

## Install htop

```sh
sudo apt install htop
```

## Display running processes

```sh
htop
```
