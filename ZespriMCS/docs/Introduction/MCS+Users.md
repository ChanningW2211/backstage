# **MCS Users**
- [Grower](#grower)
- [Packhouse Employee](#packhouse-employee)
- [Orchard Packhouse Contact](#orchard-packhouse-contact)
- [MCS Packhouse Administrator](#mcs-packhouse=administrator)
- [Zespri Users](#zespri-users)
- [Zespri MCS Support Users](#zespri-mcs-support-users)
- [Zespri MCS Administrator Users](#zespri-mcs-administrator-users)
- [SSP / TSP users](#ssp-tsp-users)

MCS has several user roles (which are linked to permissions) which relate to the user functions:

- Grower
- Packhouse Employee
- Orchard Packhouse Contact (all of them are Packhouse Users/Employees)
- MCS Packhouse Administrator
- Zespri User
- Zespri MCS Support User
- Zespri MCS Administrator User
- Sampling Service Providers (SSP Users)
- Testing Service Providers (TSP Users)

Most of the users in the system are synchronised from CRM and use a Canopy Id for login (ADFS external\xxx logins). Default roles are also assigned in CRM. 

MCS also supports Zespri domain users logging in directly without having their user details sync’d. The system checks for existence of one of 3 AD groups in the ADFS token and grants access based on the group permission.
## **Grower**
Are owners, managers or otherwise involved in the running of kiwifruit orchards 

- They all have access to MCS but don’t all use the system 
- They are mainly focussed on the Sample Results/Reports
- All have a relationship with one or more Packhouses

They are responsible for the following data in MCS:

- Orchard master data - Orchard name, Orchard address, Orchard contact name/number/email
- Hazards for Maturity Clearance & sampling purposes 
## **Packhouse Employee**
Are users from Packhouses that manage the maturity clearance process.

- Are the main system users
- They add and remove Orchard Part-Blocks
- Create and manage maturity areas
- Add/update maps
- Add/update hazards (not technically responsible for them though)
- Raise almost all maturity clearance Sample Requests
- Review results and reports, trends in the fruit quality
- Plan for harvesting based on the status and fruit quality detailed in the reports (specific Packhouse users, not all of them)
- Organise the Clearance to Pack (CTP) process
## **Orchard Packhouse Contact**
An Orchard Packhouse Contact is a subset of Packhouse Employee that is associated with specific KPINs as the nominated Packhouse Contact. Their details are sent with every SR for their KPIN and they appear on the main KPIN screen under the Packhouse tabs. All OPCs are Packhouse Employees. OPC was not supposed to be a separate role in the system.
## **MCS Packhouse Administrator**
Are the administrators in the Packhouse. They are called MCS Packhouse Administrator to differentiate between CRM users that are

- Responsible for their users' access levels in MCS (not able to change these in MCS yet)
- Same as Packhouse Users - no real system difference at this point
- In future will be able to manage Packhouse Users and their permissions
## **Zespri Users**
Zespri domain users are able to log in to MCS using their standard Zespri account.

This is based on belonging to one of several AD Groups specific to MCS.

- Users are read only by default

AD Group:

- Resource\_MCS\_user (PROD)
- Resource\_MCS\_TST\_user (DEV, TST, PPE)
## **Zespri MCS Support Users**
Are the Zespri Support Desk for MCS and Maturity Clearance. Can be either from Zespri AD or CRM. 

- First level support for MCS (ability to impersonate any non-admin user)
- Raise incidents to Qrious for Level 2 triage
- Raise Monitoring, Residue and Audit samples
- Are responsible for ensuring SRs are allocated correctly to Service Providers
- Monitor/manage incoming measures from TSPs
- Manage Role Overrides where a user requires different permissions than default
## **Zespri MCS Administrator Users**
Are the super users for the MCS system. Can be either from Zespri AD or CRM.

- Limited to around 4 people at Zespri
- Responsible for admin data in the system:
  - Clearance Criteria
  - Sample Test Groups
  - Dispensation Rules
  - SR allocation rules
- Granting/denying MA dispensations
- Managing Service Provider allocations and verifying % splits
- Verifying the fruit results are as expected
- Releasing results to the industry at a set time every day during season
- Manage Role Overrides where a user requires different permissions than default

AD Group:

- Resource\_MCS\_user (PROD)
- Resource\_MCS\_TST\_user (DEV, TST, PPE)
## **SSP / TSP users**
Only SSP or TSP users with MCS access are system users for access to the eAPIs

See eAPI section for more details: [eAPI - Sampling and Testing Service Provider API](https://sparknz.atlassian.net/wiki/spaces/BIGDATA/pages/10427793639/eAPI+-+Sampling+and+Testing+Service+Provider+API)
