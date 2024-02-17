# How to serve a Node.js application hosted in an AWS EC2 Instance through a web server like Nginx?

Serving a Node.js application through a web server like Nginx can provide various benefits like better performance, security, and the ability to run multiple applications on the same server.

Here's a step-by-step guide to serve a `Node.js` application on an **AWS EC2 instance** using `Nginx`:

1. **Install Node.js:** If you haven't installed `Node.js` on your **EC2 instance**, you'll need to do that first. You can use **package managers** like `apt` for **Ubuntu** or `yum` for **Amazon Linux** to install `Node.js`.

2. **Install Nginx:**

On Amazon Linux:

```text
sudo yum install nginx
```

Start Nginx:

```text
sudo systemctl start nginx
```

Enable Nginx to start on boot:

```text
sudo systemctl enable nginx
```

3. Configure Nginx for Your Node.js Application:

Create or modify an **Nginx server block configuration**. A common practice is to create a new **configuration file** for **each site** in `/etc/nginx/sites-available/` and then create a **_symbolic link_** to it in `/etc/nginx/sites-enabled/`.

```text
sudo nano /etc/nginx/sites-available/my-node-app
```

Using `nano` Add the following **configuration**:

```text
server {
    listen 80;

    server_name petboarder.com www.petboarder.com;

    location / {
        root /home/ec2-user/CEN4090L_Capstone_Project/dist;
        index index.html
        try_files $uri $uri/ =404;
        proxy_pass http://localhost:3000; # Assuming your app runs on port 3000
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

**Save** and **close** the file. Create a **symbolic link** to the `sites-enabled` directory:

```text
sudo ln -s /etc/nginx/sites-available/my-node-app /etc/nginx/sites-enabled/
```