\# Project 3: Install the Web Server and Database Software



\## Objective



Install and verify the software required to host the school website on the Ubuntu server. The server uses the LAMP stack: Linux, Apache, MySQL, and PHP.



\## Apache Web Server



Apache was installed and configured to start automatically on boot.



The Apache service was verified as active and running.



The server was confirmed to be listening on TCP port 80.



The Droplet IP address was accessed through a web browser and Apache successfully served web content.



\## MySQL Server



MySQL Server was installed successfully.



The MySQL service was verified using:



`sudo systemctl status mysql`



The service reported:



`active (running)`



The MySQL secure installation process was completed using:



`sudo mysql\_secure\_installation`



Recommended security settings were applied.



\## PHP



PHP and the common extensions required by the website were installed.



The PHP installation was verified using:



`php -v`



Installed PHP version:



`PHP 8.3.6`



PHP execution through Apache was also tested successfully using a temporary PHP information file.



The temporary PHP information file was removed after testing to avoid exposing server configuration information.



\## Verification



The following acceptance criteria were verified:



\- Apache is installed and serving web content.

\- The server is listening on TCP port 80.

\- MySQL Server is active and operational.

\- PHP 8.3.6 is installed.

\- PHP executes successfully through Apache.

\- The temporary PHP information page was removed after verification.



\## Result



The Ubuntu server now has a working LAMP stack and is ready for the next stage of the school website hosting project.

