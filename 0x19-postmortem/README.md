Issue Summary
12/09/2023 From 10:00 AM to 12:00 AM UTC+1 all requests for the homepage to our servers got a 403 response when they access the payment platform on the website
Timeline
10:00 AM : Got an alert from PagerDuty
10:15 AM : Medium time to acknowledge by the on call team 
10:25 AM : Successful change rollback
10:44 AM : Server Restarts begin
11:20 AM :  Debugging the problem
11:50 AM : Probelm fixed and pushed the changes
 11:55 AM : Server restart begins
 12:00 AM : 100% traffic back online with the new updates
Root cause 
The root cause was a malware infection which caused the .htaccess file to be constantly corrupt
Resolution
After rolling back changes, we found out that the issue was from our apache. Since our hosting platform was Hostinger, using the Hostinger File Manager, we accessed the .htaccess file which was available at the public-html directly.
We created a backup file for the .htaccess file by downloading the file.
After the download, we deleted the main .htaccess file.

Also, since there might be a malware infection which will keep injecting unwanted code to the .htaccess file, we used a malware scanner plugin to identify any malicious software on our website
 
12:00 AM : 100% of trafic back online with the new updates
Corrective and preventative measures
To prevent similar problems from happening again we will
Create an automated test pipeline 
Add a monitoring software to our servers which will monitor lot of things and one of them Network Traffic requests 
Create a tests for every new update and the teams should not push until those tests pass


