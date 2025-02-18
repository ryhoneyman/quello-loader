# Quello Loader - Project Quarm Character Database Loader

Scripts used to export Project Quarm character data to Quello API / Character Viewer

## Setup
* Copy ./etc/quello.conf.skel to ./etc/quello.conf and edit the values for database access and upload url/key.  The quello.conf file should be CHMOD 600 and CHOWN to a service account or elevated user as this is a privileged variable file that contains database passwords.
* ./bin/quello-update is used to clone the database tables that will be used in the dump for upload.  By cloning the tables, we won't lock the main game tables during dump.  This script should be run from crontab on a schedule determined by the server admin.  It may be beneficial to run this daily during non-peak hours to minimize potential performance disruption.  The crontab user that is designated to execute the script must be able to access the quello configuration file.
* ./bin/quello-dump is used to create a file containing all the cloned data and then uploads the data to the API receiver endpoint.  This script can be chained with the quello-update script in the crontab to immediately run after it finishes, or it can be a separate entry that runs at a time interval after the update finishes.  The crontab user executing this script must also be able to access the quello configuration file.