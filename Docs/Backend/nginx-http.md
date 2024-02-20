# How to set up a http reverse proxy for a Node.js application hosted in an AWS EC2 Instance through using Nginx:

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

3. **Configure Nginx for Your `Node.js` Application:**

Create or modify an **Nginx server block configuration**. A common practice is to create a new **configuration file** for **each site** in `/etc/nginx/sites-available/` and then create a **_symbolic link_** to it in `/etc/nginx/sites-enabled/`.

```text
sudo nano /etc/nginx/sites-available/my-node-app
```

Using `nano` Add the following **configuration**:

```text
server {
    listen 80;

    server_name pet-boarder.com www.pet-boarder.com;

    /home/ec2-user/CEN4090L_Capstone_Project/dist       # website's root directory
    index index.html;                                   # default index file

    location / {
        proxy_pass http://localhost:3000;               # Assuming your app runs on port 3000
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

4. Update the `/etc/nginx/nginx.conf` file to load the `index.html`  in the **project root folder** instead of the default nginx file.

```text
# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log notice;
pid /run/nginx.pid;

# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;

events {
    worker_connections 1024;
}

http {
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    server {
        listen       80;
        listen       [::]:80;
        server_name  www.pet-boarder.com;
        root         /home/ec2-user/CEN4090L_Capstone_Project/dist;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
                proxy_pass http://localhost:3000; # Assuming your app runs on port 3000
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }

# Settings for a TLS enabled server.
#
#    server {
#        listen       443 ssl http2;
#        listen       [::]:443 ssl http2;
#        server_name  _;
#        root         /usr/share/nginx/html;
#
#        ssl_certificate "/etc/pki/nginx/server.crt";
#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
#        ssl_session_cache shared:SSL:1m;
#        ssl_session_timeout  10m;
#        ssl_ciphers PROFILE=SYSTEM;
#        ssl_prefer_server_ciphers on;
#
#        # Load configuration files for the default server block.
#        include /etc/nginx/default.d/*.conf;
#
#        error_page 404 /404.html;
#        location = /404.html {
#        }
#
#        error_page 500 502 503 504 /50x.html;
#        location = /50x.html {
#        }
#    }
}
```

5. **Test Nginx Configuration:**

Before applying the changes, you should check the configuration for syntax errors:

```text
sudo nginx -t
```

If everything is okay, you should see a **message** indicating that the **configuration test** is **successful**.

6. **Restart Nginx:**

* Apply the **configuration changes** by restarting Nginx:

```text
sudo systemctl restart nginx
```

7. **Update Security Groups:**

* Ensure that your EC2 instance's security group allows incoming traffic on port 80 (for HTTP) and 443 (for HTTPS, if you're planning on setting up SSL).

8. **Start Your Node.js Application:**

* Run your `Node.js` application, ensuring its listening on the **port** specified in the **Nginx configuration** (in this example, port `3000`).

9. (Optional) Set Up SSL:

* If you want to serve your application over HTTPS, you can use `Certbot` to obtain a free **SSL certificate** from `Let's Encrypt`. `Certbot` has **plugins** that work with `Nginx`, making it easy to **obtain** and **install certificates**.

By now, you should be **able to access** your `Node.js` **application** through your **domain** *without specifying the port*, and `Nginx` will **proxy the requests** to your `Node.js` application.

## Online Resources:

* [The NGINX Crash Course](https://youtu.be/7VAI73roXaY?si=_E5ezH0rXXCKnPh7)
* [How to Setup Nginx Reverse Proxy for Node.js Application](https://youtu.be/YH0guj1kFxI?si=hbCpdB29C6nx159y)