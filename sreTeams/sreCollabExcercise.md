# SRE Collaboration with Development Teams

Have a look at the Software Release Process diagram created by the development manager. The development manager's message is, "if a change passes QA testing, then it ought to be released." Apply your knowledge about error budgets and provide a compelling explanation as to why this is always not true.
Given that the application uses multiple systems (databases, cloud infrastructure), it may not always be the application code at fault when the error budget is consumed. Define ways to keep the application's releases stable.

# Solution

Question 1

QA does not typically test in production, and if there is, it's usually very light testing. Additionally, if the SRE team crosses its threshold of 50% ops work, the additional work is shifted to the development team. So the thought pattern of "if it passes QA, it's released" can be true as long as the 50% threshold is not violated. However, depending on the size and scope of the changes, all of the 50% could be used in one release, which would slow the development team's release cadence. While everyone agrees testing is the only way of knowing what the software will do and how the new changes interact with the existing system, a better approach would be to make the releases isolated, contain small changes, and release more often. This would make for more stable releases and keep the error budget intact.

Question 2

smaller more frequent releases -- smaller changes are faster and easier to fix, identify rollback, should an incident arise

isolated changes -- these changes can be quickly identified and corrected if an incident arises

feature flags -- this is probably the best way since it can be controlled, and it's isolated to a subgroup of users.
