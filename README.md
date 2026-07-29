# RBAC-and-ABAC

* ACL -> Is this specific user on this resource’s access list?
* RBAC -> What role does this user have?
* ABAC -> Do the user, resource, and environment attributes satisfy the policy?

### RBAC
- Identify resources/modules — Users, Payroll, Leave, Reports.
- List actions — Read, Create, Update, Delete, Approve.
- Create business roles — Employee, Manager, HR, Finance, Admin.
- Map permissions to roles — Decide what each role can do.
- Enforce access centrally — Middleware/API permission checks + audit logs.

### ABAC
- Identify resource attributes — Department, Owner, Classification, Clearance.
- Identify user attributes — Department, Role, Clearance, Employment type.
- Identify environment attributes — Time, Device, IP, VPN, MFA status.
- Define boolean access policies — Example: same department AND office hours AND MFA verified.
- Use a central policy engine — Evaluate rules at request time and log allow/deny decisions.

* **RBAC learning:** [Role Based Access Control (RBAC) -> gfg](https://www.geeksforgeeks.org/ethical-hacking/role-based-access-control-1)
* **ABAC learning:** [Attribute Based Access Control (ABAC) -> gfg](https://www.geeksforgeeks.org/system-design/attribute-based-access-controlabac)
* **ACL learning:** [Access Control List (ACL) -> gfg](https://www.geeksforgeeks.org/operating-systems/difference-between-access-control-list-and-capability-list)

# ACL vs RBAC vs ABAC

| Aspect | ACL | RBAC | ABAC |
|---|---|---|---|
| Main idea | Per-resource access list | Role-based access | Attribute- and context-based access |
| Main question | "Is this user on this resource's list?" | "What role does this user have?" | "Do user, resource, and environment attributes satisfy the policy?" |
| Access unit | User ↔ Resource | User ↔ Role ↔ Permission | User + Resource + Action + Environment |
| Example rule | Alice can edit File A | Managers can approve leave | Finance managers can read finance files during office hours from company devices |
| Granularity | Very fine (per item) | Medium | Very fine and dynamic |
| Needs resource attributes? | No (resource identity only) | No (usually) | Yes |
| Needs user attributes? | Only user identity | Role | Many attributes |
| Needs environment attributes? | No | No | Yes |
| Policy complexity | Low | Low–Medium | High |
| Administration effort | High when many resources exist | Low | Medium–High |
| Scalability | Poor–Medium | Good | Good |
| Performance | Fast | Fast | Slower |
| Best for | File/document sharing | Enterprise apps and admin systems | Banking, healthcare, government, zero-trust systems |
| Typical storage | ACL entries on each resource | Roles and permission tables | Attributes and policy engine |
| Real-world analogy | Guest list on a room door | Staff badge | Smart security gate |

# Same Scenario: "Can Alice open Salary.pdf?"

## Decision process

| Model | Decision process |
|---|---|
| ACL | Check whether Alice is listed on Salary.pdf. |
| RBAC | Check whether Alice's role has payroll.read permission. |
| ABAC | Check Alice's department, clearance, time, device, network, and MFA status against policy. |

## Non-technical analogy (office)

| Model | Office analogy |
|---|---|
| ACL | Names written on a meeting-room guest list. |
| RBAC | "Manager" badge opens manager rooms. |
| ABAC | Door opens only if you are a manager, it is working hours, and your ID and device are verified. |

## Planning focus in production

| Model | Top planning focus |
|---|---|
| ACL | Resource ownership and sharing lists |
| RBAC | Roles and permission catalogue |
| ABAC | Attributes and business policies |

## What most real systems use

| System | Common approach |
|---|---|
| Google Drive | ACL + RBAC |
| WordPress admin | RBAC |
| GitHub repositories | RBAC + ACL |
| Hospital records | RBAC + ABAC |
| Banking systems | RBAC + ABAC |
| Cloud IAM (AWS/Azure/GCP) | RBAC + ABAC |

## One-line memory trick

| Model | Remember as |
|---|---|
| ACL | This person on this item |
| RBAC | This job can do this |
| ABAC | This person can do this on this item in this situation |
