# Who SRE's work with
It really depends on the organization but the teams you work with could include:

Development -- you will probably interface with this team the most, as there are a lot of overlapping tasks.
DevOps -- since DevOps typically owns the delivery of software, they will be interested to know how well it is performing for end users.
QA -- SRE and QA may have more of a consulting relationship since both teams use automation
Support -- this team is on the front line with clients and may need a hand from SRE teams for more technical issues.

When a company creates a website or web service that is available for users to connect to and consume, unforeseen events happen which cause the operations of the site or service to be interrupted. These include:

Connection problems
Unavailability of the service
Errors within parts of the service
Teams need to respond in order to restore the service. Without an SRE team, other teams share parts of the ops work, leaving Ops fragmented and disorganized. For example, the Development team may have documentation on how to resolve an issue, and the Sysadmin may not know about it.

This also takes away from the different team's primary focus, which could cause them to miss delivery dates or the implementation of new technology. With an SRE team, the ops work is centralized to one team, freeing up the other teams to focus on their responsibilities. And the SRE team would own and manage the Ops work, making the resolution of issues more efficient and streamlined.

# Core skills of SRE
In this lesson, we will learn how to distinguish unique SRE roles and responsibilities within an enterprise. This includes the following topics:

Identify the formation of SRE in the industry.
What is SRE? Where did it come from?
Compare the SRE scope of work and functions vs. adjacent roles (DevOps, Sysadmin, and developers)
Many of the responsibilities are shifting. We will learn which ones typically fall into the SRE category and which belong to other roles.
Explain core skills of SRE, which include:
Monitoring & tooling
Information gathering
Latency, saturation, errors, traffic
Implementing system updates
Release coordination
Creating an infrastructure to ensure the reliability of services
By the end of this lesson, you will know the origins of SRE, its primary scope of work and be able to identify and explain the core skills.

# The Need For SRE
The industry and market have embraced the idea of SRE. Even though SRE has been around for a while, it has been only recently that the demand for it has grown.

After a slow start, SRE job growth is taking off. Although there is no evidence that points to a single catalyst for the growth around 2017, there are contributing factors such as:

Increased adoption -- due to the growth of online services; this is apparent in late 2019 and early 2020
The success of SRE Teams -- Businesses are catching wind of how effective SRE teams are at mitigating risk and reducing the downtime of service, and want to adopt teams of their own.
There are more and more companies with open SRE positions and new positions being created every day.

# Formation of SRE in Industry

Throughout history and even today, many companies relied upon teams of System Administrators to handle maintaining application and computing systems. These teams were responsible for ensuring software applications and dependencies were properly orchestrated into a product or service.

They were also tasked with updating, responding to events as they occurred. Once the product/service swells in size and complexity, the team expands to account for the growth.

Given these tasks that sysadmins had to account for, their skills are vastly different than those of developers who are responsible for writing and maintaining the application code.

Thus, a division occurs between the developers and sysadmins into two teams: development and operations.

The term "SRE" was first coined in 2003 by Benjamin Treynor Sloss, who worked as a programmer at Google. He was responsible for heading up a team of seven engineers to ensure Google websites were highly available, failure-proof, and accessible.

The team's focus was on engineering because without constant engineering, the load on the operations team will increase, and the team will need more people to keep pace with the load.

# SRE Scope Of Work 

When we think of SRE, Operations comes to mind--SRE is responsible for ensuring everything is running smoothly. The things that SRE's are responsible for include:

Incident Response -- responding to incidents in production environments
Post-mortems -- root cause analysis, preventing the issue in the future
Monitoring & Alerting -- creating and using dashboards and alerting mechanisms
Capacity Planning -- planning new infrastructure to accommodate application demands
DevOps responsibilities include:

Software delivery -- the correct version of the software is in the proper environment
Release Automation -- no human needed to release software
Configuration management -- configuring environments to support a software application
Infrastructure as Code (IaC) -- storing environment configurations in source control
SysAdmins responsibilities include:

Access control -- creating user accounts and assigning permissions to those
User training -- showing users how to use the software needed to complete daily job tasks
Backup/Restore of data -- ensuring data is backed up and can be restored should a disaster happen
Automating routine tasks -- one example is purging old emails
Documentation -- this includes system configuration, backup/restore process, and user roles/access
Developers responsibilities include:

Meeting client requirements -- coding these requirements in the development phase of the SDLC
Creating unit tests -- quick tests to ensure their logic is behaving the way it should be
System requirements -- analyze and provide system requirements to run their application
Documentation -- most of the documentation they provide are comments within code

# Core Skills of SRE

The core skills of SRE are:

Monitoring -- creating dashboards to display the status of the system

Information Gathering -- compiling pertinent information like log files and software versions and sharing with the SRE and development teams

The "Golden 4" -- latency, saturation, errors, traffic (see new terms below)

Updating The System -- planning and coordinating system upgrades, security updates, or regular patches

Release Coordination -- gather everything needed for the release of the next version of the application

Creating Infrastructure -- providing an environment for the system to operate