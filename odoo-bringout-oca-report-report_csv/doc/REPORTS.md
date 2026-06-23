# Reports

Report definitions and templates in report_csv.

```mermaid
classDiagram
    class ReportCSVAbstract
    AbstractModel <|-- ReportCSVAbstract
    class PartnerCSV
    AbstractModel <|-- PartnerCSV
```

## Available Reports

No named reports found in XML files.


## Report Files

- **__init__.py** (Python logic)
- **report_csv.py** (Python logic)
- **report_partner_csv.py** (Python logic)

## Notes
- Named reports above are accessible through Odoo's reporting menu
- Python files define report logic and data processing
- XML files contain report templates, definitions, and formatting
- Reports are integrated with Odoo's printing and email systems
