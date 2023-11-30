# Enterprise Workflows
This is the suggested ranking for the tasks:

Configuration management would be the first task I would try to fully automate. This could be used as a place to automate other things in a uniform fashion. I foresee pushing the script library or the cron jobs into configuration management.
The script library would come next because the task is already automated, it's just a matter of executing it. These seem like a quick win and would provide a substantial amount of benefit.
I would push the fully automated cron jobs into configuration management to centralize those tasks.
Log file removal would be targeted next. Log files that are not rotated can consume disk space and cause the system to fail because of a full disk.
The password reset workflow seems like a quick win to fully automate.
OS/System patches -- these patches can be anything from upgrades or security patches. Fully automating this could be pushed into configuration management
Database Server patches -- these patches can be anything from upgrades or security patches. Fully automating this could be pushed into configuration management
If users only need reports every so often like monthly, I would keep the reporting process at this spot in the list. If the application was a reporting system and everyone involved in the reporting process experienced pain on a regular basis, I would move it to the top 5.
Archive data retrieval -- this seems like a feature for a very small subset of users; if that is the case, it stays where it is in the list, if not, it would move further up in the list just after the reporting process.
Data updates--this may prove difficult to fully automate, which is why it's so far down in the list.
Send emails to users -- rather than keep the code base around that sends emails, researching a way to offload this would probably be best.
Database schema updates -- The only toil I could identify with this example is that this process may not be centralized, but given the risk this poses and the fact that it's fully automated already, I would leave this right where it is.