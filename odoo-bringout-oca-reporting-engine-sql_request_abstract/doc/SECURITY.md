# Security

Access control and security definitions in sql_request_abstract.

## Access Control Lists (ACLs)

Model access permissions defined in:
- **[ir.model.access.csv](../sql_request_abstract/security/ir.model.access.csv)**
  - 3 model access rules

## Record Rules

Row-level security rules defined in:

## Security Groups & Configuration

Security groups and permissions defined in:
- **[ir_module_category.xml](../sql_request_abstract/security/ir_module_category.xml)**
- **[res_groups.xml](../sql_request_abstract/security/res_groups.xml)**
  - 2 security groups defined

```mermaid
graph TB
    subgraph "Security Layers"
        A[Users] --> B[Groups]
        B --> C[Access Control Lists]
        C --> D[Models]
        B --> E[Record Rules]
        E --> F[Individual Records]
    end
```

Security files overview:
- **[ir.model.access.csv](../sql_request_abstract/security/ir.model.access.csv)**
  - Model access permissions (CRUD rights)
- **[ir_module_category.xml](../sql_request_abstract/security/ir_module_category.xml)**
  - Security groups, categories, and XML-based rules
- **[res_groups.xml](../sql_request_abstract/security/res_groups.xml)**
  - Security groups, categories, and XML-based rules

Notes
- Access Control Lists define which groups can access which models
- Record Rules provide row-level security (filter records by user/group)
- Security groups organize users and define permission sets
- All security is enforced at the ORM level by Odoo
