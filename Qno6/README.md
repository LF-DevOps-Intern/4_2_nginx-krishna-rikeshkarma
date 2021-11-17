# Install LEMP stack (avoid installing MySQL) and open info.php on port 80 and print message info.php.

- A software stack is a set of software tools bundled together. LEMP stands for Linux, Ngnix, MySQL, and PHP, all of which are open source and free to use. It is the most common software stack that powers dynamic websites and web applications. Linux is the operating system; Ngnix is the web server; MySQL is the database server and PHP is the server-side scripting language responsible for generating dynamic web pages.
- For our task, we don’t need to install MySQL as per the question.
- Our operating system is already Linux so we don’t have to install one and we have already installed Nginx previously, so this leaves us to installing PHP only.
- To install PHP on our system we can use the following command in our terminal:
  - `sudo apt install php-fpm`
  ![installing php](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno6/snapshots/installing%20php.png)

- Now we need to create a new directory for the localhost, for this, we can invoke the following command in the terminal:
  - `sudo mkdir /var/www/php`
- Then create simple info.php page using the following command:
  - `sudo nano /var/www/php/info.php`
- Add the following lines in the file we just created.
  ![sample info php file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno6/snapshots/sample%20infophp%20file.png)
- We need to create php.conf file inside /etc/ngnix/sites-available using the following command:
  - `sudo nano /etc/nginx/sites-available/php.conf`
  - And add the following lines of code in the php.conf file:
  - As port 80 has already been used, lets use port 90 for this task.
  ![php conf file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno6/snapshots/php%20conf%20file.png)
- Let’s create a soft link, which helps Nginx to read from the startup using the following command:
  - `sudo ln -rs /etc/nginx/sites-available/php.conf /etc/nginx/sites-enabled/`
- Now let’s test and restart Nginx using the following command:
  - `sudo nginx -t`
  - `sudo systemctl restart nginx`
  ![create link test and restart nginx](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno6/snapshots/create%20link%20test%20and%20restart%20nginx.png)
- We can now observe info.php.
  ![observe info php](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno6/snapshots/observe%20info%20php.png)
