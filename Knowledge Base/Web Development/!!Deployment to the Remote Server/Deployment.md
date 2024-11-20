1. Create instance
2. Add public SSH key (somewhere in instance settings)
3. Connect via SSH
```bash
ssh-add ~/.ssh/id_rsa # path to private key
ssh d.dzmitryeu@35.203.154.224
```
4. Open port 3000
	  - Go to the Firewall rules in the Google Cloud Console: [https://console.cloud.google.com/networking/firewalls/list](https://console.cloud.google.com/networking/firewalls/list?_ga=2.269097073.1459891523.1616667818-1721081090.1616089653)
	  -  Click the "Create firewall rule" button at the top of the page.
	  -  You need to give the rule an arbitrary lowercase name
	  -  An arbitrary tag (we used `port3000`), and this source IP range: `0.0.0.0/0`.
	  -  The range is important! This will remove the limit on connecting to the server from only specific IP addresses, so that your project could be checked by code reviewers.
	  -  Below, add a tcp port 3000
	  -  Click "Create" and make sure that the new port is now added to the list of Firewall rules.

5. To make this rule apply to the VM we've created, we now just have to add the `port3000` tag to our VM. Go back to the Compute Engine > VM Instances page, and click on the name of your instance to go to its page. Click the "Edit" button. Then add `port3000` to the list of tags, and press "save" at the bottom of the page.
6. ### Install Node
```bash
# Run these on the VM

# In this command, replace 15 with the major version number
# of Node.js that is installed on your computer locally
curl -sL https://deb.nodesource.com/setup_15.x | sudo -E bash -

# installing Node.js
sudo apt-get install -y nodejs
```
The first command gets a list of packages for the official distribution of Node.js, while the second command installs those packages on our system.

7. ### Install MongoDB
```bash
# Run these on the VM

# 1.
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -

# 2.
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list

# 3.
sudo apt-get update

# 4.
sudo apt-get install -y mongodb-org
```

When the last command finishes, let's make sure that MongoDB is installed. The following command will run the mongo server:

```bash
# Run this on the VM
sudo service mongod start
```

We'll also need to make it so that the mongo server will launch automatically even when the remote machine restarts:

```bash
# Run this on the VM
sudo systemctl enable mongod
```

Now we should be able to start the mongo shell by entering the next command:

```bash
# Run this on the VM
mongo
```

8. ### Install Git
```bash
# Run these on the VM

# 1.
sudo apt update

# 2.
sudo apt install git
```

9. ### Domain name
![[Pasted image 20220112120742.png]]
https://api.infostash.students.nomoreparties.sbs
http://infostash.students.nomoreparties.sbs



10. npm install
11. npm run start - проверить, что все запускается
12. ### Install PM2
	```bash
	# Run this on the VM
	sudo npm install pm2 -g
	pm2 start app.js
	```
	
	Let's make the application start even when the server restarts. To make this happen, enter this command:
	```bash
	pm2 startup
	
	# To setup the Startup Script, copy/paste the following command:
	sudo env PATH=$PATH:/usr/bin /usr/lib/node_modules/pm2/bin/pm2 startup systemd -u practicum --hp /home/practicum
	
	pm2 save
	```
	
	### Setup NGINX
	
```bash
sudo apt update #updates the list of packages
sudo apt install -y nginx #installs nginx, -y approves all the prompts automatically
```

### Ubuntu firewall
```bash
sudo apt install ufw
```

configure firewall
```bash
sudo ufw allow 'Nginx Full'
sudo ufw allow OpenSSH
```

The command `sudo ufw allow 'Nginx Full'` opens two ports on the current machine — `80` and `443`. These two ports receive HTTP and HTTPS requests coming to the server. The command `OpenSSH` opens port `22` which establishes an SSH connection so that we can connect to the server via the console even with the firewall turned on.

After that, turn on the firewall:
```bash
sudo ufw enable
```

### Launch NGINX and set it to automatically start:
```bash
sudo systemctl enable --now nginx
```

### Change the NGINX configuration file

```bash
sudo nano /etc/nginx/sites-available/default

# sudo allows us to execute a command as a super user
# nano is a text editor
# /etc/nginx/sites-enabled/default is a path to the NGINX configuration file
```

```bash
server {
  server_name api.infostash.students.nomoreparties.sbs;

  location / {
    proxy_pass http://localhost:3001;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }

}

server {
  server_name infostash.students.nomoreparties.sbs www.infostash.students.nomoreparties.sbs;

  root /home/practicumuser/around-frontend;

  location / {
    try_files $uri $uri/ /index.html =404;
  }

}

```

Restart NGINX

```bash
# check configuration
sudo nginx -t

sudo systemctl reload nginx
```

Allowing long server names

```bash
sudo nano /etc/nginx/nginx.conf
```

Add inside http block
```server_names_hash_bucket_size 128;```

### SSL
Run this command on the command line on the machine to install Certbot.

```bash
sudo snap install --classic certbot

```

Execute the following instruction on the command line on the machine to ensure that the `certbot` command can be run.

```bash
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

Enter this command to connect the issued certificate:

```bash
sudo certbot --nginx
```

Restart NGINX

```bash
sudo systemctl restart nginx
```

13. Git pull
14. pm2 restart app
