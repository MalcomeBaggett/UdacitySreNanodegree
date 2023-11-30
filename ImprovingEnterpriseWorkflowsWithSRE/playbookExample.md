PLAYBOOK EXAMPLE

Tied to alert [ALERT_NAME]

Summary:

The application and web services intermittently fail to connect to the database and need to be restarted. Check the logs for connection failures and restart the application.

Summary of architecture:

There is a web application [NAME] and a web service [NAME] that connect to a SQL Database [NAME and LOCATION OF SQL DATABASE]

Log Locations
Error log
/var/log/myapp/myapp-error.log
/var/log/myapp-service/myapp-service.log
Application log
/var/log/myapp/myapp.log
Remediation Steps:

Login to [SERVER_NAME] and run the myapp-restart.sh script. Once myapp restarts, run the myapp-service.sh script. The connection to the database should be restored. Verify successful connections in the log files.

