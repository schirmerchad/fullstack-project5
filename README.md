# Fullstack Project #5 / Linux Server Configuration

Udacity Fullstack Nanodegree Project 5 ssh -v grader@52.11.176.33 -p2200 password: grader

# Project Requirements 

Your README.md file should include all of the following:

i. The IP address and SSH port so your server can be accessed by the reviewer.

ii. The complete URL to your hosted web application.

iii. A summary of software you installed and configuration changes made.

iv. A list of any third-party resources you made use of to complete this project.

# Connection Instructions

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

# Third-Party Resources

remeber to restart ssh after config changes!

ssh -i ~/.ssh/id_rsa grader@52.10.18.139 -p 2200 (to login as grader)
or ssh grader@52.10.18.139 -p 2200
grader pw: grader
postgres pw: catalog
