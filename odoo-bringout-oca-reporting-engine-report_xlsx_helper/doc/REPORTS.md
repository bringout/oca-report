# Reports

Report definitions and templates in report_xlsx_helper.

```mermaid
classDiagram
    class ReportXlsxAbstract
    AbstractModel <|-- ReportXlsxAbstract
    class TestPartnerXlsx
    AbstractModel <|-- TestPartnerXlsx
```

## Available Reports

No named reports found in XML files.


## Report Files

- **__init__.py** (Python logic)
- **report_xlsx_abstract.py** (Python logic)
- **report_xlsx_format.py** (Python logic)
- **test_partner_report_xlsx.py** (Python logic)

## Notes
- Named reports above are accessible through Odoo's reporting menu
- Python files define report logic and data processing
- XML files contain report templates, definitions, and formatting
- Reports are integrated with Odoo's printing and email systems
