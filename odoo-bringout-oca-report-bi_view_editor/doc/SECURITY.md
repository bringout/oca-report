# Security

Access control and security definitions in bi_view_editor.

## Access Control Lists (ACLs)

Model access permissions defined in:
- **[ir.model.access.csv](../bi_view_editor/security/ir.model.access.csv)**
  - 4 model access rules

## Record Rules

Row-level security rules defined in:
- **[rules.xml](../bi_view_editor/security/rules.xml)**

## Security Groups & Configuration

Security groups and permissions defined in:
- **[res_groups.xml](../bi_view_editor/security/res_groups.xml)**
  - 1 security groups defined
- **[rules.xml](../bi_view_editor/security/rules.xml)**

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
- **[ir.model.access.csv](../bi_view_editor/security/ir.model.access.csv)**
  - Model access permissions (CRUD rights)
- **[res_groups.xml](../bi_view_editor/security/res_groups.xml)**
  - Security groups, categories, and XML-based rules
- **[rules.xml](../bi_view_editor/security/rules.xml)**
  - Security groups, categories, and XML-based rules

Notes
- Access Control Lists define which groups can access which models
- Record Rules provide row-level security (filter records by user/group)
- Security groups organize users and define permission sets
- All security is enforced at the ORM level by Odoo
