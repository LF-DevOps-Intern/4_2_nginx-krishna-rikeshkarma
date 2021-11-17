# Install Nginx and host a simple index.html with the message “Hello Nginx”
  - Let’s update our machine first using the following command:
    - `sudo apt-get update`<br/>
  ![updating our machine](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/updating%20our%20machine.png)
  - And to install Nginx we just need to invoke the following command in the terminal:
    - `sudo apt-get install nginx`<br/>
  ![installing nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/installing%20nginx.png)
  - We can check to verify the installation by using the following command:
    - `nginx -v`<br/>
  ![verifying the installation](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/verifying%20the%20installation.png)
  - Now after installation, we need to enable our firewall using the command:
    - `sudo ufw enable`<br/>
  ![enable our firewall](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/enable%20our%20firewall.png)
  - Now since we have installed our firewall we can list the application configuration that our firewall knows, so for that we need to use the following command:
    - `sudo ufw app list`<br/>
  ![list firewall app configuration](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/list%20firewall%20app%20confiigurations.png) 
    - After using this command we will see all the available applications our Nginx applications - ‘Nginx Full’, ‘Nginx HTTP’ and ‘Nginx HTTPS’.
  - Let’s allow all of them so that all the encrypted and unencrypted traffic is allowed. So for this lets just use the following commands:
    - `sudo ufw allow ‘Nginx Full’`
    - `sudo ufw allow ‘Nginx Http’`
    - `sudo ufw allow ‘Nginx Https’`<br/>
  ![firewall allowing nginx services](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/firewall%20allowing%20nginx%20services.png)
    - Based on whatever kind of traffic we want ot allow we can make sure the application has been enabled.
  - Now we can check the status by typing:
    - `sudo ufw status`<br/>
  ![checking firewall status](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/checking%20firewall%20status.png)
  - We can see that ngnix, http and Https are allowed. This means they are completely fine and they are working.
  - To check if our ngnix server is working or not we can just type in the command:
    - `sudo systemctl status nginx`<br/>
  ![nginx status](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/nginx%20status.png)
  - We can check on the browser as well by typing _localhost_ on the browser's address bar.<br/>
  ![nginx on browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/nginx%20on%20the%20browser.png)

We can see that the service/ server is running perfectly.

  - Now to host a simple index.html with the message “Hello Nginx”.
    - Firstly we need to create a directory for localhost by invoking the command:
      - `sudo mkdir -p /var/www/localhost/html`
    - Then we need to create a new HTML file named index.html for our sample page using the command:
      - `nano /var/www/localhost/html/index.html`
    - Now let’s configure the HTML file to display the message “Hello Nginx”<br/>
  ![configure HTML file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/configure%20HTML%20file.png)
    - Afterwards need to create _localhost.conf_ file inside _/etc/nginx/sites-available_ using the following command:
      - `sudo nano /etc/nginx/sites-available/localhost.conf`
    - Then we need to add the following lines of code inside the localhost.conf file:
        ```
        server {
          listen 80;
          listen [::]:80;
          root /var/www/localhost/html;
          index.html index.nginx-debian.html;
          server_name localhost;
          location / {
            try_files $uri $uri/ =404;
          }
        }
        ```
  ![configure localhost config file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/configure%20localhostconf%20file.png)

  - Now we need to enable the file by creating a link that Nginx will read from during the startup, using the following command:
      - `sudo ln -s /etc/nginx/sites-available/localhost/ /etc/nginx/sites-enabled/`
    - We can test by using the command:
      - `sudo nginx -t`
    - Let’s restart Nginx using the command:
      - `sudo systemctl restart nginx`


Finally, let’s check if our simple index.html file is up and running:<br/>
  ![sample index file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno1/snapshots/sample%20index%20file.png)
