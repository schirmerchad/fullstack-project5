# Fullstack Project #5 / Linux Server Configuration

With this app I took a baseline installation of a Linux distribution on a virtual machine and prepared it to host a web application. This included installing updates, securing it from a number of attack vectors and installing/configuring web and database servers.

# Connection Instructions
* IP Address: 52.10.18.139
* SSH Port: 2200
* AWS URL: http://ec2-52-10-18-139.us-west-2.compute.amazonaws.com

# Software Installed
Apache software and packages
* `apt-get install apache2`
* `apt-get install python-setuptools libapache2-mod-wsgi`
* `apt-get install libapache2-mod-wsgi python-dev`
* `apt-get install a2enmod wsgi`

Git
* `apt-get install git`

Python
* `apt-get install python-pip`

PostgreSQL
* `apt-get install postgresql`

Flask, SQLalchemy, Oauth2
* `apt-get install python-psycopg2 python-flask`
* `apt-get install python-sqlalchemy python-pip`
* `pip install oauth2client`
* `pip install requests`
* `pip install httplib2`
* `pip install flask-seasurf`

# Configuration Changes Made
1. Create a user `grader`
  * `adduser grader`
  * `visudo` and add grader to users with sudo capabilities
2. Update all packages
  * `apt-get update`
  * `apt-get upgrade`
3. Change SSH port
  * `nano /etc/ssh/sshd_config` and enable password authentication
  * `ssh-keygen` on local machine to generate new ssh key for grader
  * `scp ~/.ssh/id_rsa.pub grader@52.10.18.139:` to securely copy the ssh key to the linux server
  * `su - grader` to substitute user to grader
  * `mkdir ~/.ssh` to make .ssh directory
  * `chmod 700 ~/.ssh` to allow owner to read, write, and execute
  * `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys`
  * `rm ~/id_rsa.pub`
  * `chmod 600 ~/.ssh/authorized_keys` to allow owner to read and write
4. Configure UFW
  * `ufw default deny incoming`
  * `ufw default allow outgoing`
  * `ufw allow 2200/tcp`
  * `ufw allow 80/tcp`
  * `ufw allow 123/udp`
  * `ufw enable`
5. Change local timezone to UTC
  * `dpkg-reconfigure tzdata`
6. Install and configure Apache2
  * Properly install Apache2 and dependency packages
  * `nano /etc/apache2/sites-available/app.conf` and add a virtual host declaration for the Python app
  * `a2ensite app` to enable the specified site within the apache configuration
  * `nano /var/www/app/app.wsgi` and add a WSGI file to use the Apache module to host the Python app
7. Install and configure PostgreSQL
  * Properly install PostgreSQL
  * `cd /etc/postgresql/9.3/main/`
  * `su - postgres`
  * `psql`
  * `CREATE USER catalog WITH PASSWORD 'password';`
  * `ALTER USER catalog CREATEDB;`
  * `CREATE DATABASE catalog WITH OWNER catalog;`
  * `REVOKE ALL ON SCHEMA public FROM public;`
  * `GRANT ALL ON SCHEMA public TO catalog;`
8. Clone and setup Catalog app project
  * `git clone https://github.com/schirmerchad/mealCost.git`
  * `rm README.md`
  * `mv project.py __init__.py`
  * `mv * ..`
  * `rm -rf FSND-P5`
  * The database_setup.py, mealdatabase.py, and __init__.py files require a refactoring to use PostgreSQL instead of SQLite3 and reference the new file path for client_secrets.json
  * Update the authorized JavaScript Origins in the Google Developers Console to reflect the URLs for the app

# Third-Party Resources

ssh -i ~/.ssh/id_rsa grader@52.10.18.139 -p 2200 (to login as grader)
or ssh grader@52.10.18.139 -p 2200
grader pw: grader
postgres pw: catalog
