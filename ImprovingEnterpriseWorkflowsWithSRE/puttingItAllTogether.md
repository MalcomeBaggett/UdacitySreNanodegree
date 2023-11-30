# Exercise: Putting it All Together
Create an outline of a playbook for a web application that has frequent outages. Include items to check for:

The application itself
The underlying infrastructure
Be sure to include any helpful commands or processes to assist in the problem diagnosing process.
The website is down, and you are the one to respond. Luckily, you used the playbook you recently created and were able to keep the outage to a minimum.

Explain how having the playbook and using it could reduce the length of time it takes to correct an outage.
Explain how potentially automating the steps in a playbook could reduce cost and toil.
If the outage lasted 30 minutes, how much would that cost the company? Hint: use $5900 per minute.

# Solution
Check for connectivity to the website.
Check that the DNS name resolves by doing an nslookup <website>
Bring up dashboards for the host metrics of the webserver, API servers, database servers.
Check connectivity from the webserver to any API servers or database servers.
Locate scheduled tasks that may interface with the website on the utility server utility-server.mycompany.com
Check the logfile located at /var/log/application/app.log
Check the config file located at /etc/application/config/app.config
Look at the release version and confirm it matches with the one from the last deployment.
Check for any corresponding services the website uses to operate, and ensure those are enabled.
SSL cert
Having the playbook gives someone the location of log/config files, outlines commands used to diagnose connectivity, provides other information about extraneous systems that may interface with the application, and enables someone without application knowledge but computer skills to rule out common causes of incidents. Having the steps or a checklist of items speeds up the process because there is no need to look for pertinent files or try to understand how the application works.

While a human executing the steps in a playbook is good, having this done with automation would speed up the diagnostic processes. The steps in a playbook would be completed in a fraction of the time allowing for the human to look for the more complex underlying issues. One factor of incident response is speed because while the service has an outage, it costs money and adds to user frustration. Automating the playbook will enable speed and reduce the toil, reduce the incident response time, and would ultimately reduce cost.


A 30 minute outage would cost $177,000. (30 * $5900 = $177,000)