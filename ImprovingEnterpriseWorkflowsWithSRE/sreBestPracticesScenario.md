# SRE Best Practices

The data science team has finished making a machine learning (ML) application. It uses a database, front-end UI, a handful of APIs and has a reporting mechanism to email users the results. The team has followed the release checklist and has outlined:

The amount of volume. Since it will only be released to a few select beta groups, they expect the volume to be small. The users sign in, configure the machine learning, and the configuration is stored in the database. Any data the machine learning uses is also stored in the database as well and is retrieved via API calls.

Integration into the existing network -- the team has a DNS name and coded the ML program to support load balancing and custom monitoring metrics.

Failure modes -- some of the APIs have been identified as sources of failure, while others include retry logic.

Automation -- there is a custom job that needs to be created in order to launch the reports to the users. It needs to be configured to run ad-hoc.

Rollout -- the ML program supports a canary deployment, although there is only one database.

The ML program is set to be deployed off-hours to reduce risk. During the deployment, an incident occurs, and the SRE on-call responds. Due to this being a new program, there has not been a playbook created, so the engineer calls others to assist, including some of the team who created the ML program. After finding out the issue was a misconfigured connection string to the database, the engineer begins creating the postmortem document. It looks something like this:

Impact: Low impact, new software product release, a small number of beta users were affected

Mitigation steps: Update the connection string to the proper settings for production

Root cause: The connection string was misconfigured because it was not included in the configuration management tool

Prevention measures: Ensure this update is present in the configuration management tool

Follow up with the ML team in a meeting to review this issue.

Example Postmortem Template

Summary
Impact:

[Summary of the users impacted and length of time]

Root Cause:

[Description of the issue]

Technical Summary
Mitigation Steps

[Step 1]
[Step 2]
Prevention Measures:

[Describe what is being done to prevent a future outage]

Summary/Notes:

[Summary of the incident or extra notes]

Attach Data/Graphs


Launch Checklist

Architecture/Volume
Provide an architecture diagram of request/response flow.

Attach the load test results.

Integration
DNS name(s) created

[DNS Name 1]
[DNS Name 2]
LoadBalancer rules

[LoadBalancer identifier] - [Rule 1]
[LoadBalancer identifier] - [Rule 2]
Monitoring configuration has been provided

[Install monitoring agent on VM]
[Open firewall port on VM for monitoring agent]
[Import dashboard into monitoring system]
Single-points of failure
[There is only one API that talks to the database]
[There is no retry logic]
Manual processes documented
[Init script needs run before the app is intstalled]
[Job needs to be configured to support reports]
Description or actions of a rollback strategy
[Step 1]
[Step 2]
[Step 3]

# Enterprise Workflows

## Toil is defined as:
Overhead -- completing a number of sub-tasks prior to running the actual task

Manual Intervention -- if the computer can complete the task just as well or better than a human, then the human ought to step aside and let the computer do its job.

Repetitive Tasks -- things that need human intervention over and over again, either on a regular schedule (like running a monthly report) or reacting to a server constantly having a disk full of log files

Any task that takes a reaction and interrupts a human.

## Eliminating Toil

Eliminating toil in any organization:

Using reliable product launches provides the following advantages:

Easily implemented
No software or training
Launch checklist
Supports quick decisions
Reduces time spent managing releases
Monitoring

Provides visibility into the system & an alerting mechanism
Dashboard of “the golden 4”
Provide the team ways to decide how to fix problems associated with the golden 4
Examples include:
Using load balancers
Adding servers when demand is high
Automated traffic routing
Fixing errors in the application
Overall benefits:

No consultants
No expensive software packages
Some of the most popular monitoring tools are free
Focus on processes
Use a release checklist and monitoring system
