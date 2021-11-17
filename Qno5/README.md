# Reverse proxy all HTTP traffic of port 82 to port 85.


- Firstly let’s create a _reverse_proxy82to85.conf_ inside _/etc/nginx/sites-available_ using following command:
  - `sudo nano /etc/nginx/sites-available/reverse_proxy82to85.conf`
- Then add the following on the conf file we just created.<br/>
  ![reverse_proxy82to85 file]()
- Let’s create a soft link to the sites-enabled directory, which helps Nginx to read from the startup using the following command:
  - `sudo ln -rs /etc/nginx/sites-available/reverse_proxy82to85.conf /etc/nginx/sites-enabled/`
- Now let’s test and restart Nginx using the following command:
  - `sudo nginx -t`
  - `sudo systemctl restart nginx`
  ![create link test restart ngnix]()
- We can observe “Test is successful.” at port 85.<br/>
  ![observer at port 85]()
