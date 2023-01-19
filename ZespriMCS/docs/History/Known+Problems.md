# **Known Problems**
A number of key people who held knowledge on MCS have moved on from Qrious. There are large first-hand knowledge gaps and we think no one knows how some internal parts of the engine work. A lot of the business logic is in stored procedures that were written by Benet who has already left. Some information about the Calc Engine and its sprocs: [MCS metric calculations (Calc Engine)](https://sparknz.atlassian.net/wiki/spaces/BIGDATA/pages/10394698115)

There were some bad design/architecture decisions made in the past. For example, access system is partially role-based, part attribute-based. This has led to a complicated understanding of who can access what and how new access should be granted. This is important to understand for our largest piece of work for the 2023 season as we are required to add a new access role.

Zespri systems are prone to access problems (getting access takes days or weeks; can randomly disappear). Zespri are also very stringent about granting access and treat our team as independent contractors. Zespri controls everything in the project and Qrious employees need individual access to a few different systems. e.g. Zespri controls the project Jira boards, which we need access to view and complete work. All code repositories are hosted in Zespri’s Azure DevOps and have an Azure SQL DB which also requires connections they manage.

Zespri changes specific details of business rules from time to time; e. g. in 2021 they’ve asked to change the time threshold after which SRs are assigned not to next day but to the day after that, in 2022 they’ve changed it back. They need these changes to support the changes on the market. Business rules lack documentation and means extra care must be taken when making changes in the system, as we have no visibility

At some point the person responsible for the Zespri system disappeared at the very beginning of the season, and the company could not pay growers for quite a while. We should avoid this at all costs by documenting everything that is not documented yet. Zespri may hold some negative opinions or ‘bad blood’ towards Qrious over this.

In the past, lack of middle management has led to direct contact between Zespri people and Qrious developers. It was disturbing the workflow and distracted the developers.


