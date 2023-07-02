# Simple Notes App
This is a simple notes app built with React and Django. Open Source Repo by Shubham Londhe.

## Nginx
Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
`sudo systemctl enable nginx`
`sudo systemctl start nginx`
`sudo systemctl status nginx`

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/bwarikoo/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app:1.0 .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:1.0
```

## Changes to be made in nginx configuration to serve the application
The app is running on port 8000 by default. We can utilize nginx to serve as a Reverse Proxy for the app without allowing traffic on port 8000. 

Changes to be made in default config file located at `/etc/nginx/sites-enable/` to add below line:

```
proxy_pass http://127.0.0.1:8000;
```
Restart the nginx service using command `sudo systemctl restart nginx`
