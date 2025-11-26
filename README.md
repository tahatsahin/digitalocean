- Repo for actions in droplet/digitalocean

First, add IP to /etc/hosts file to define a domain name for the droplet ip
```bash
IP_HERE	DOMAIN_NAME_HERE
```

- Then, edit $HOME/.ssh/config file to configure SSH

```bash
Host DOMAIN_NAME_HERE
	User root
	Hostname DOMAIN_NAME_HERE
	PreferredAuthantications publickey
	IdentityFile ~/.ssh/id_rsa
```

- To connect remote server
```bash
ssh root@DOMAIN_NAME_HERE
```

- To copy static files to server
```bash
rsync -e ssh /home/user/directory root@DOMAIN_NAME_HERE:/remote/user/directory/
```

- Serve static content using NGINX -> /etc/nginx/nginx.conf file 
```conf
http {
	server {
		listen 8080;
		location / {
			root /data/www;
			index index.html index.htm;
			try_files $uri $uri/ =404;
		}
	}
}
```
