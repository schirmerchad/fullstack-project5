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
  * `okay`
4. Configure UFW
5. Change local timezone to UTC
6. Install and configure Apache2
7. Install and configure PostgreSQL
8. 

# Third-Party Resources

ssh -i ~/.ssh/id_rsa grader@52.10.18.139 -p 2200 (to login as grader)
or ssh grader@52.10.18.139 -p 2200
grader pw: grader
postgres pw: catalog
