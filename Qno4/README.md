# Create a test2.conf and listen on port 82 and to “ location /test/” with the message “ Test is successful”.

- Firstly let’s create a directory for localhost by invoking the following command:
  - `sudo mkdir -p /var/www/localhost/html/test`
- Then let’s create a sample index.html file using the following command:
  - `sudo nano /var/www/localhost/html/test/index.html`
  - And write a simple HTML code inside the HTML file we just created.<br/>
  ![sample index file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno4/snapshots/sample%20index%20file.png)
- Now let’s create test2.conf file inside /etc/nginx/sites-available using following command:
  - `sudo nano /etc/nginx/sites-available/test2.conf`
  - And add the following code in the file ‘test2.conf’<br/>
  ![test2 conf file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno4/snapshots/test2conf%20file.png)
- Let’s create a soft link to enable the file, which helps Nginx to read from the startup using the following command:
  - `sudo ln -rs /etc/nginx/sites-available/test2.conf /etc/nginx/sites-enabled/`
- Now let’s test and restart Nginx using the following command:
  - `sudo nginx -t`
  - `sudo systemctl restart nginx`<br/>
  ![create link test restart nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno4/snapshots/create%20link%20test%20restart%20nginx.png)
- We can observe that we are getting the message **“Test is successful”** with _localhost:82/test_<br/>
  ![Test is successful](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno4/snapshots/Test%20is%20successful.png)
