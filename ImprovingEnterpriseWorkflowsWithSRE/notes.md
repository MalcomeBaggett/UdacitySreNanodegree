# Introduction
The key takeaway from this lesson is lowering risk. You will learn there are many approaches SRE teams use to lower risk. These approaches can seamlessly fit into business workflows because they improve efficiency and streamline processes.

In addition, you will also learn that lowering risk lowers cost, which is also another benefit of SRE teams.

# Lesson Outline

In this lesson, we will investigate enterprise workflows that can be improved with common SRE practices using cost-benefit analysis. This includes the following topics:

Identify common SRE best practices:
On-call incident response
Post-mortem
Reliable product launches
Explore enterprise workflows that can be improved with SRE:
Identify toil in an enterprise
Understand how toil is created
Use SRE best practices to reduce toil
Perform a cost-benefit analysis of SRE:
Cost & risk
Risk & SRE
SRE Costs
By the end of this lesson, you will be able to identify common SRE best practices, explore enterprise workflows that can be improved with SRE, and be able to perform a cost-benefit analysis of SRE.

# How Do Experts Think About Enterprise Workflows

SRE Teams can help us improve enterprise workflows in the following manners:

Centralize Ops work so that multiple teams are not responsible
Keep the ops work off of other teams, and ensure one team owns it. This helps refocus the IT department and enables one team to own and stabilize the operations work.
Reduce overhead and improve the efficiency of IT Departments
Automate tasks and reduce toil; with an SRE team's focus, tasks that are not normally automated can be, which helps the IT Department as a whole.
Reduce the risk of an organization
Have on-call procedures in place and playbooks. Rather than passing the on-call pager from team to team, one team can keep the pager and use playbooks to reduce the time it takes to resolve an outage.
Improve uptime
Understand the root cause of outages, and prevent them in the future. By making a conscious effort to understand and prevent an outage, it will not be repeated.

# SRE Best Practices
## On-call & incident response strategies:
Primary/secondary contacts are on-call one week a month. With a secondary contact, if you happen to be away from the phone, the call will divert to that person.
The on-call contact only handles essential events.
Instituting a "follow the sun" model to eliminate night shifts.
Limit the number of incident responses to two per shift.
Have playbooks (see the example below) that are comprised of escalation paths and incident-management procedures.

## On-call & incident response strategies:
Primary/secondary contacts are on-call one week a month. With a secondary contact, if you happen to be away from the phone, the call will divert to that person.
The on-call contact only handles essential events.
Instituting a "follow the sun" model to eliminate night shifts.
Limit the number of incident responses to two per shift.
Have playbooks (see the example below) that are comprised of escalation paths and incident-management procedures.
Post-mortems

## Post-mortems:
Events that occur which lead to the creation of post-mortems:

Data-loss
On-call engineer intervention, which comes from an alert or a phone call
Failures with monitoring or visible downtime
Items to include in a post-mortem:

A record of an incident and its impact
Actions taken to mitigate the incident
The incident root cause
Any prevention measures
Identification of the causes of system failure, not pointing fingers
Instituting a blameless post-mortem culture:

The problem and system failure
Involving everyone on the team
Collecting thoughts and solutions from smart people
Finding a permanent solution

## Reliable product releases include:
Architecture and dependencies
Latency requirements
Request flow from front-end to back-end
The volume of requests
Integration consists of:
DNS
Load balancing
Monitoring
Failure Modes** **are:
Single-points of failure
Mitigation tactics of failure within the system
Process and Automation highlights:
Any manual process
Documentation
Rollout Planning involves:
How the change goes live
Canary deployments

# Cost-benefit Analysis and SRE Impact

## SRE Teams Reduce Risk:
Live & breathe risk management
Contend with 99.99% and 99.999% up-times
Less than five minutes of allowable downtime per month.
Core functions and best practices of SRE all revolve around managing risk.

## The Cost of Downtime:
The actual cost of downtime is unknown
Recent studies estimate it between $5,600-$9,000 per minute.
99.99% uptime allows for about 4.5 minutes of downtime a month.
This equates to $25,000-$40,000 in loss per month.
99.999% uptime allows for about 26 seconds of downtime per month.

## SRE Costs:
Redundancy or adding more IT infrastructure in different geographies.

Provides capabilities such as:

Taking a server offline to perform maintenance
Implement zero-downtime deployments
Routing traffic away from a problem server during an incident

Opportunity Costs

Improving the system means not building revenue-generating features
Slows the release of new features
Regular operations work keeps SRE teams from engineering