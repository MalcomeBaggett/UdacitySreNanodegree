# Defining SRE Roles and Responsibilities

A company was looking to form a new SRE team of 5-7 engineers and asked for your help. This company already has Development teams, DevOps teams, and Sysadmin teams, and members from each team have expressed interest in joining an SRE team. The company has allowed you to invite members from each of the existing teams to take on typical SRE responsibilities. Include a Team Lead as one of the roles.

Create a diagram that shows:

The team structure
The roles on the team
The responsibilities of each role (listed)
Additionally, explain the team selection process and, most importantly, how each member from Development, Sysadmin, and DevOps filled each new SRE role.

# Solution

The team lead ensures each team member's work is scoped and contributes to the team. In other words, this person wants to ensure everyone on the team is doing what is expected of them, no side projects for different groups or taking on more responsibilities than what is asked of them. Additionally, the team lead contributes to architecture design meetings and helps form workflow for the team.

The system architect is responsible for creating infrastructure that is easily scalable and replicable. Additionally, this role documents all infrastructure, reviews existing infrastructure, highlights any shortcomings, and provides ways to eliminate those. They also make recommendations on ways to implement newer technologies and architecture and provide migration paths from existing infrastructure. The infrastructure engineer is divided between 50% development tasks and 50% operations tasks. This person controls their own destiny as far as managing operations tasks because they can potentially use 50% of their time to automate some of those tasks. This person is also responsible for planning and executing system patches and updates. The release manager is responsible for change management and code releases. When the code needs to be deployed to production, it goes to this person who ensures the code has all dependencies satisfied and ensures proper communication is sent to the stakeholders. The release manager executes the code release and any rollback procedures if needed. Lastly, the monitoring engineer is responsible for creating dashboards for essential metrics such as the "four golden signals," creating and managing alert rules, and is usually the first to know if an incident occurs. Additionally, this person manages the monitoring rules and governance for monitoring newly created or existing IT infrastructure.

DevOps -> Release Manager, Infrastructure Engineer

DevOps is already close to the releases of the software, so making one a release manager would be a smooth transition. Also, having DevOps be part of the infrastructure engineer would benefit since DevOps is close to the application code; they would understand scaling needs and be able to automate tasks.

Sysadmin -> Architect, Monitoring engineer

Sysadmin as an architect would be a smooth transition since Sysadmins deal with IT systems as part of their responsibilities. They understand the necessary components for IT systems to work together and would be able to easily produce architecture to support an application. Also, with their knowledge of infrastructure, a monitoring engineer would be a good fit for a sysadmin since they would understand networking, how to manage traffic load, and how to easily gather data about the system or application.

Developer -> Infrastructure Engineer, Monitoring Engineer A developer as an infrastructure engineer would be a benefit since they could help on creating IaC (infrastructure as code). Also, having a developer as a monitoring engineer would benefit since they could quickly diagnose issues with the application and find log files if an incident were to happen.

# SRE Team Mission

The benefits of a team mission/vision include:

Shared approach
Strategy
Direction to solving a problem
Providing benefits more significant than the team itself
Higher work satisfaction
Less conflict
Teams are made up of people, and people have their own beliefs and values. Values guide decisions, and decisions guide behavior. A newly formed team must establish core values that are agreed upon by team members. The benefits include:

Building trust
Providing psychological safety
Embracing risk
Providing a sense of inclusion
After a team is formed and the core values are set, a survey is taken to identify the factors that a team encounters. This is typically done by using a SWOT analysis. SWOT stands for:

Strengths -- characteristics of the team that give it an advantage over other teams

Weaknesses --characteristics of the team that give it a disadvantage to others

Opportunities -- elements in the environment that the team could exploit to its advantage

Threats -- elements in the environment that could cause trouble for the team

Once this exercise has been completed, it ought to paint a picture of the team's capabilities and provide discussion topics on alignment, coordination, and workflows. From this, goals can be formed, and from those goals, the mission can be defined.
