# Quello Loader - Project Quarm Character Database Loader

Scripts used to export Project Quarm character data to Quello API / Character Viewer

### Requirements
* curl 
* mysqldump
* gzip

## Setup
* Copy ./etc/quello.conf.skel to ./etc/quello.conf and edit the values for database access and upload url/key.  The quello.conf file should be CHMOD 600 as this is a privileged variable file that contains database passwords.
* ./bin/build-quello-grants is used to print the MySQL GRANT statements required for the user specified in the quello.conf file.  One time executable, only prints.
* ./bin/quello-dump is used to create a file containing all the appropriate data and then it uploads the data to the API receiver endpoint.  This script should be run from the crontab at intervals determined by the admin.  The crontab user executing this script must also be able to access the quello configuration file.