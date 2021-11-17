# Reverse proxy all HTTP traffic of port 82 to port 85.


- Firstly let’s create a _reverse_proxy82to85.conf_ inside _/etc/nginx/sites-available_ using following command:
  - `sudo nano /etc/nginx/sites-available/reverse_proxy82to85.conf`
- Then add the following on the conf file we just created.<br/>
  ![reverse_proxy82to85 file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno5/snapshots/reverse_proxy82to85%20file.png)
- Let’s create a soft link to the sites-enabled directory, which helps Nginx to read from the startup using the following command:
  - `sudo ln -rs /etc/nginx/sites-available/reverse_proxy82to85.conf /etc/nginx/sites-enabled/`
- Now let’s test and restart Nginx using the following command:
  - `sudo nginx -t`
  - `sudo systemctl restart nginx`
  ![create link test restart nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno5/snapshots/creat%20link%20test%20and%20restart%20nginx.png)
- We can observe “Test is successful.” at port 85.<br/>
  ![observer at port 85](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno5/snapshots/observe%20at%20port%2085.png)
