# Northwind Services: Entra ID User and Group Lab
## Project summary

I created 16 fictional Northwind staff and contractor accounts in Microsoft Entra ID, plus my separate administrator account. I organized the Northwind users into department security groups and created a Helpdesk role group. I kept contractors in their own group, added Alex Morgan to the Sales group, and set Daniel Brooks as Alex’s manager. I verified that the directory shows 17 accounts and the Sales group has 5 members. I also saved screenshots of user and group audit logs in this repository. The four-app example above is hypothetical; I did not assign applications in Entra ID.

## Project overview

This project documents a Microsoft Entra ID lab for a fictional company, Northwind Services. I created user accounts, organized users into assigned security groups, and captured audit log evidence.

## What I built

- Created 16 initial Northwind staff and contractor accounts, then added Alex Morgan as an additional Sales user.
- Created department security groups named `SEC-Dept-<Department>` for Executive, IT, Finance, Sales, HR, and Contractors.
- Created `SEC-Role-Helpdesk` for the help desk function.
- Added users to the groups that match their department or role.
- Set Alex Morgan’s manager to Daniel Brooks and added Alex to `SEC-Dept-Sales`.
- Captured screenshots of user and group audit logs.

The directory also contains my administrator account. It is separate from the Northwind staff and contractor accounts.

## Why use groups?

Groups make it easier to organize people and manage access. For this example, assume five Sales users need four hypothetical apps: Northwind CRM, Northwind Expenses, the Sales Proposal Library, and the Sales Dashboard. Connecting the Sales group to those apps would mean four group-to-app assignments; assigning each person separately would mean 20 assignments. This comparison is hypothetical; I did not assign apps in Entra ID..

## Evidence and documentation

- [Group and naming design](docs/org-design.md)
- [Naming conventions](docs/naming-convention.md)
- User and group audit log screenshots are in the `screenshots/` folder.

## What I learned

- Creating a group does not automatically add people to it; membership must be assigned.
- Manager information is set on a user account separately from group membership.
- Audit logs can show successful directory changes.
- Checking the Users list and group membership helped me verify the results.

## Future improvements

For a larger organization, I would consider dynamic groups, scheduled access reviews, and a managed process for removing contractors when their contracts end. These were not configured in this lab.
