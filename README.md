# fullstack-project5

Linux-Server-Configuration
Udacity Fullstack Nanodegree Project 5 ssh -v grader@52.11.176.33 -p2200 password: grader

Procedure

(1) Set up Linux server as Instructed by Udacity

Udacity Account

(2) Create a new user named grader

Source

Create user grader

$ adduser grader
(3) Give the grader the permission to sudo

Source

Edit sudoers file to allow grader to sudo

$ visudo
Find the line

root ALL=(ALL:ALL) ALL
and add

grader ALL=(ALL:ALL) ALL
below it

ssh -i ~/.ssh/id_rsa grader@52.25.181.161 -p 2200 (to login as grader)
or ssh grader@52.25.181.161 -p 2200
