# Web-serving on vIC

We take the Web-serving benchmark from CloudSuite (http://cloudsuite.ch/webserving/) as an example, to demonstrate how customers who are interested in the LEMP implementation of a cloud native web-serving application could use our guidelines to deploy the system on vIC 0.7.0 with Docker Compose. This demo has three tiers deployed on three containerVMs: an Nginx Web server, a Memcached server, and a Mysql database server. The Web server runs Elgg (a social networking engine) and connects the Memcached server and the database server through network.

## Workflow

### Build docker image for the Web server

In the original the Web-server docker image from Cloudsuite, the functionality of “email verification for new user registration” is not enabled, which makes it less realistic and practical. Therefore, we need make some modifications and re-build the docker image for the Web server. You can also skip this step and pull the pre-built docker image from Docker Hub (wangcheng86/wangcheng86:web_mail_enabled).
Step I: 
Download the original installation files from https://github.com/ParsaLab/cloudsuite/tree/master/benchmarks/web-serving/web_server
Step II:
In Dockerfile, add “Run apt-get install –y sendmail” and “EXPOSE 25”
Step III:
Replace “bootstrap.sh” with the following:

