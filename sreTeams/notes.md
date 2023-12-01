# SRE Teams

When individuals work together, they have to collaborate amongst themselves. They also need to collaborate with other teams. This is no different for an SRE team.

Defining the individual roles and responsibilities of an SRE team, as well as negotiating ways for two teams to get along, is what this lesson is all about.

# Lesson Outline

In this lesson, we will learn how to define an optimal SRE team structure and work allocation given business needs. This includes:

Illustrating collaboration best practices with the development team
Measuring tension between Development & SRE Teams
Explore ways development introduces less risk in releases
Defining the SRE Team
Optimal team size
Review roles and responsibilities
Developing governance of SRE teamwork quality
Identify the structure and components of a productive SRE team
Team SWOT Analysis
By the end of this lesson, you will be able to define an SRE team, identify the structure and components, and show collaboration best practices with the development teams.

# How Do Experts Think About SRE Teams?

To review, Development teams want

Code releases to go to production
Deliver new features for stakeholders for feedback
That way, the development cycle continues and the product gets better with every iteration.

At the same time, SRE teams want to maximize uptime. This means:

Minimizing risk
Not changing production
Or changing it as little as possible to ensure stability.

So what do both of these teams do well, and how do they collaborate?

Both engineer solutions -- there is a lot of overlap here, and many opportunities to consult with each other on various ways to solve problems.
Both want to do a good job, so quality is always in their minds. Development wants their features to work correctly, and SRE wants the same for their automation. Lastly, both
Teams want a positive customer experience. This is why each team does what they do.

So for example, the development team wants to release a sought-after feature for the stakeholders. This requires the deployment of new code to production, and production is owned by the SRE team, which sees the release as risky. If the development team can convince the SRE team that the new feature will not cause production to have an outage, the new feature can be released. Otherwise, the teams will need to work together to find a solution that benefits both of them.

# SRE Collaboration with Development Teams

Ways to measure the inherent tension (which we have already learned about) between product development teams and SRE have emerged. Here are the ways this tension is measured:

Software fault tolerance
Code structure -- using modular blocks of code makes it easier to debug and fix errors.
Exception handling -- programming for “what if”
Retry logic -- e.g., if a connection is lost, the program retries until successful.
Software Testing
Unit testing -- basic levels of testing which evaluate code logic
Integration testing-- testing software modules as a group
System testing -- testing the entire software system
Frequency of Deployments
More deployments = more feedback on code
Enables the team to deliver value to stakeholders more quickly
Incorporate testing to provide quality code
Error Budgets:
A happy medium between the teams,
Determines how unreliable an application can be within a quarter of a year.
The product team sets an expectation of uptime,
The SRE team measures the uptime
Actual uptime vs expected uptime is compared.
If the actual uptime > expected uptime, new releases might be pushed
If the actual uptime < expected uptime, new releases are halted
So 99.99% allows for approximately 52 minutes of downtime per year, or 13 minutes a quarter. If the development team's release causes an outage for 5 minutes, then they would have 8 minutes left in the error budget for the quarter and can still release software. If the release causes 13 or more minutes of downtime, releases are halted for the rest of the quarter. This error budget resets to 13 minutes in the next quarter.

Development Strategies for Mitigating Risk
Feature flags are code blocks that can be toggled on or off for a subset of users. The idea is to have a select group of users test the new feature, then roll it out to a wider audience in a later release.

Releasing more minor changes more frequently: changes may only be a few lines of code or a small function of the application. If an incident were to occur, it's easy to diagnose and fix.

Isolating changes: changes may only affect the database or the UI of the website, for example. If an incident were to occur, it's easy to diagnose and fix. Rolling back the change would only affect one component.

# Defining SRE Roles and Responsibilities

SRE Team Structure:
The SRE team structure will vary from company to company. The ideal size is five, and this number will be used throughout the part of this lesson. There are five distinct roles:

## Team Lead:

Directs the work
Keeps team focused
Contributes to architecture meetings
Forms workflows of the team

## System Architect:

Create scalable infrastructure
Document/Diagram infrastructure
Make recommendations for new technologies
Provide migration paths to new technology
This role would use IaC (Infrastructure as Code) tools to provision infrastructure and diagramming tools.

## Infrastructure Engineer:

50% development tasks, 50% operations tasks
Can use their time to automate Ops tasks
Planning/executing system patches/updates
This role would use different scripting languages to automate tasks, as well as configuration management tools like Ansible.

## Release Manager:

Change management
Code releases
Ensures code has all dependencies satisfied
Executes the release, and rollback procedures
This role would use a CI/CD tool along with the source control tool to ensure the code could be released or rolled back, as well as verify the correct changes.

## Monitoring Engineer:

Creating dashboards
Managing alerting rules
Usually first to know of an incident
Manages monitoring rules/governance for new/existing IT infrastructure
This role would use monitoring software such as Prometheus/Grafana or be most interested in the dashboarding/alerting features of other types of monitoring software.
