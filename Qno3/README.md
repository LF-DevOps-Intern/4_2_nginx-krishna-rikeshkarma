# Nginx Reverse proxy all HTTP requests to nodes js API.

- A proxy server is a go‑between or intermediary server that forwards requests for content from multiple clients to different servers across the Internet. A reverse proxy server is a type of proxy server that directs client requests to the appropriate backend server. It provides an additional level of abstraction and control to ensure the smooth flow of network traffic between clients and servers.

- To reverse proxy Nginx all HTTP requests to node js API, firstly let’s start the pm2 tool on the first API during the previous assignment using the following command:
  - `sudo pm2 start index_api1.js`<br/>
  ![start pm2 tool on our nodejs app](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno3/snapshots/start%20pm2%20tool%20on%20our%20nodejs%20app.png)<br/>
  ![nodejs app on browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno3/snapshots/nodejs%20app%20on%20browser.png)

- Now lets create a reverse_proxy.conf file inside /etc/nginx/sites-available using the command:
  - sudo nano reverse_proxy.conf
  - And add the below code in the reverse_proxy.conf file:
      ```
      server {
          listen 81;
          server_name localhost;

          location / {
              proxy_pass http://localhost:6080;
          }
      }
      ```
      ![reverse_proxy configuration file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno3/snapshots/reverse_profy%20configuration%20file.png)
        

- Let’s create a soft link to the sites-enabled directory, which helps Nginx to read from the startup and enable this reverse proxy using the command:
  - `sudo ln -rs /etc/nginx/sites-available/reverse_proxy.conf /etc/nginx/sites-enabled/`

- Then let’s test and restart Nginx and check using the following commands:
  - `sudo nginx -t`
  - `sudo systemctl restart nginx`<br/>
  ![create link test restart nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno3/snapshots/create%20link%20test%20restart%20nginx.png)

- Now we can see on the browser that Nginx reverse proxy is up and running.
  ![checking reverse proxy on browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno3/snapshots/checking%20reverse%20proxy%20on%20browser.png)
