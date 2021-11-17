# What are Nginx header security and its uses? And also implement in the test.conf file.

### [The answer to the theoretical part of this question is on the assignment-pdf document on the home of this repository.](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Nginx%20Assignment%20Solution%20-%20Rikesh%20Karmacharya.pdf)

- To implement Nginx Security Headers in the _test.conf_ file, we need to add some of these headers into our localhost.conf file to implement those securities:
  - Firstly let’s navigate to _/etc/nginx/sites-available_
  - Then use the following command and add the security headers:
    - `sudo nano localhost.conf`<br/>
  ![security headers added](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno2/snapshots/security%20headers%20added.png)
    - Added the security headers.
- Now let’s create a link from it to the sites-enabled directory, from which Nginx will read from startup using the following command:
  - `sudo ln -rs /etc/nginx/sites-available/localhost.conf /etc/nginx/sites-enabled/`
- Now let’s test:
  - `sudo nginx -t`
- Then restart the Nginx service:
  - `sudo systemctl restart nginx`
  - Let’s check the status of Nginx by:
    - `sudo systemctl start nginx`<br/>
  ![nginx status after adding security headers](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno2/snapshots/nginx%20status%20after%20ading%20security%20headers.png)

- Now we can check our security headers on our browsers as well:
  - For that let’s open our browser and navigate to our localhost.
  - Then on the web browser, Inspect > Network > Headers
  - We can observe the output in the browser with implemented securities.<br/>
  ![Headers on browser](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-rikeshkarma/blob/master/Qno2/snapshots/headers%20on%20browser.png)
