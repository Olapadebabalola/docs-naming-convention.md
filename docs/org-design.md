# Northwind Services: Directory and Group Design

## Design overview

Northwind has 15 staff and contractors across Executive, IT, Finance, Sales, HR, and Contractors. I used assigned security groups named `SEC-Dept-<Department>` for those departments, plus `SEC-Role-Helpdesk` for the help desk function. Department groups provide a stable way to organize people and can be used as a starting point for access decisions. Role groups represent work that can cross department boundaries. Membership is assigned manually in this lab; no applications have been assigned to these groups.

| Group | Purpose |
| --- | --- |
| `SEC-Dept-Executive` | Executive department membership; the role is currently held by one person but is expected to be filled as the company grows. |
| `SEC-Dept-IT` | IT department membership. |
| `SEC-Dept-Finance` | Finance department membership, including payroll and invoicing roles. |
| `SEC-Dept-Sales` | Sales department membership. |
| `SEC-Dept-HR` | HR department membership, including onboarding and offboarding roles. |
| `SEC-Dept-Contractors` | Keeps contractors visibly separate from employee departments so their access can be reviewed and removed when their contracts end. |
| `SEC-Role-Helpdesk` | Represents the help desk job function, which may be staffed from IT or another department. It currently has one member because this role group is intended to represent a continuing function, not a specific person. |

## Why organize by department

Departments are a useful baseline because they are familiar, relatively stable, and match the `Department` user attribute. Consistent values also make it possible to consider dynamic membership later. Department alone is not enough for every access decision: people may need access across departments for a role, project, location, or sensitivity level. `SEC-Role-Helpdesk` demonstrates that a role-based group can complement the department groups. In a real deployment, each group should receive only the access its members need, and membership should be reviewed.

## Contractor decision

Contractors are placed in `SEC-Dept-Contractors` rather than being assumed to have the same access as employees in a department. This makes contractor membership easy to identify and review. Their fixed end dates should be tracked, and access should be removed when a contract ends. The current lab uses manual membership and does not automate expiry or offboarding.

## What changes at 500 people

At 500 people, I would keep the group naming and attribute standards, but reduce manual maintenance. With the required Entra ID P1 licensing, I would evaluate dynamic department groups driven by validated department attributes. I would also add a managed contractor lifecycle, scheduled access reviews, and centralized audit-log retention. I would pilot each change and verify membership and access before relying on it broadly.

## What I learned and corrected

My first CSV attempt did not increase the user count, and the bulk results view was empty, so it did not prove that the import had run. I corrected the CSV workflow and verified the result by checking the users list: it showed 16 accounts, including the administrator account. I also learned that manager assignment is separate from bulk user creation and that group creation alone does not add members; I verified the Sales group after adding members and saw four users listed.

The directory uses assigned security groups on the free tenant. Dynamic membership, application assignment, and automated contractor expiry are future work, not capabilities built in this lab.
