# RBAC-and-ABAC

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

RBAC learning {https://www.geeksforgeeks.org/ethical-hacking/role-based-access-control-1}
ABAC learning {https://www.geeksforgeeks.org/system-design/attribute-based-access-controlabac}
