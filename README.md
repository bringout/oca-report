# OCA Report

This repository contains **45** OCA packages for report.

## Packages Included (45 packages)

- **odoo-bringout-oca-mis-builder-mis_builder** - From mis: builder_mis_builder
- **odoo-bringout-oca-mis-builder-mis_builder_budget** - From mis: builder_mis_builder_budget
- **odoo-bringout-oca-mis-builder-mis_builder_demo** - From mis: builder_mis_builder_demo
- **odoo-bringout-oca-report-print-send-base_report_to_label_printer** - From report: print_send_base_report_to_label_printer
- **odoo-bringout-oca-report-print-send-base_report_to_printer** - From report: print_send_base_report_to_printer
- **odoo-bringout-oca-report-print-send-base_report_to_printer_mail** - From report: print_send_base_report_to_printer_mail
- **odoo-bringout-oca-report-print-send-pingen** - From report: print_send_pingen
- **odoo-bringout-oca-report-print-send-pingen_env** - From report: print_send_pingen_env
- **odoo-bringout-oca-report-print-send-printer_zpl2** - From report: print_send_printer_zpl2
- **odoo-bringout-oca-report-print-send-printing_simple_configuration** - From report: print_send_printing_simple_configuration
- **odoo-bringout-oca-report-print-send-remote_report_to_printer** - From report: print_send_remote_report_to_printer
- **odoo-bringout-oca-reporting-engine-base_comment_template** - From reporting: engine_base_comment_template
- **odoo-bringout-oca-reporting-engine-bi_sql_editor** - From reporting: engine_bi_sql_editor
- **odoo-bringout-oca-reporting-engine-bi_view_editor** - From reporting: engine_bi_view_editor
- **odoo-bringout-oca-reporting-engine-bi_view_editor_spreadsheet_dashboard** - From reporting: engine_bi_view_editor_spreadsheet_dashboard
- **odoo-bringout-oca-reporting-engine-report_async** - From reporting: engine_report_async
- **odoo-bringout-oca-reporting-engine-report_company_details_translatable** - From reporting: engine_report_company_details_translatable
- **odoo-bringout-oca-reporting-engine-report_context** - From reporting: engine_report_context
- **odoo-bringout-oca-reporting-engine-report_csv** - From reporting: engine_report_csv
- **odoo-bringout-oca-reporting-engine-report_display_name_in_footer** - From reporting: engine_report_display_name_in_footer
- **odoo-bringout-oca-reporting-engine-report_generate_helper** - From reporting: engine_report_generate_helper
- **odoo-bringout-oca-reporting-engine-report_label** - From reporting: engine_report_label
- **odoo-bringout-oca-reporting-engine-report_paperformat_company_dependent** - From reporting: engine_report_paperformat_company_dependent
- **odoo-bringout-oca-reporting-engine-report_py3o** - From reporting: engine_report_py3o
- **odoo-bringout-oca-reporting-engine-report_py3o_fusion_server** - From reporting: engine_report_py3o_fusion_server
- **odoo-bringout-oca-reporting-engine-report_qr** - From reporting: engine_report_qr
- **odoo-bringout-oca-reporting-engine-report_qweb_decimal_place** - From reporting: engine_report_qweb_decimal_place
- **odoo-bringout-oca-reporting-engine-report_qweb_element_page_visibility** - From reporting: engine_report_qweb_element_page_visibility
- **odoo-bringout-oca-reporting-engine-report_qweb_encrypt** - From reporting: engine_report_qweb_encrypt
- **odoo-bringout-oca-reporting-engine-report_qweb_field_option** - From reporting: engine_report_qweb_field_option
- **odoo-bringout-oca-reporting-engine-report_qweb_parameter** - From reporting: engine_report_qweb_parameter
- **odoo-bringout-oca-reporting-engine-report_qweb_pdf_cover** - From reporting: engine_report_qweb_pdf_cover
- **odoo-bringout-oca-reporting-engine-report_qweb_pdf_watermark** - From reporting: engine_report_qweb_pdf_watermark
- **odoo-bringout-oca-reporting-engine-report_qweb_signer** - From reporting: engine_report_qweb_signer
- **odoo-bringout-oca-reporting-engine-report_substitute** - From reporting: engine_report_substitute
- **odoo-bringout-oca-reporting-engine-report_text_format_option** - From reporting: engine_report_text_format_option
- **odoo-bringout-oca-reporting-engine-report_wkhtmltopdf_param** - From reporting: engine_report_wkhtmltopdf_param
- **odoo-bringout-oca-reporting-engine-report_xlsx** - From reporting: engine_report_xlsx
- **odoo-bringout-oca-reporting-engine-report_xlsx_helper** - From reporting: engine_report_xlsx_helper
- **odoo-bringout-oca-reporting-engine-report_xml** - From reporting: engine_report_xml
- **odoo-bringout-oca-reporting-engine-sql_export** - From reporting: engine_sql_export
- **odoo-bringout-oca-reporting-engine-sql_export_delta** - From reporting: engine_sql_export_delta
- **odoo-bringout-oca-reporting-engine-sql_export_excel** - From reporting: engine_sql_export_excel
- **odoo-bringout-oca-reporting-engine-sql_export_mail** - From reporting: engine_sql_export_mail
- **odoo-bringout-oca-reporting-engine-sql_request_abstract** - From reporting: engine_sql_request_abstract


## Installation

Install any package from this category:

```bash
# Install from local directory
pip install packages/oca-report/PACKAGE_NAME/

# Install in development mode  
pip install -e packages/oca-report/PACKAGE_NAME/

# Using uv (recommended for speed)
uv add packages/oca-report/PACKAGE_NAME/
```

## Repository Structure

Each package in this repository follows the standard Odoo addon structure:

```
oca-report/
├── odoo-bringout-oca-PROJECT-ADDON/
│   ├── ADDON_NAME/           # Complete addon code
│   │   ├── __init__.py
│   │   ├── __manifest__.py
│   │   └── ... (models, views, etc.)
│   ├── pyproject.toml        # Python package configuration
│   └── README.md            # Package documentation
└── ...
```

## Contributing

These packages are maintained as part of the [OCA (Odoo Community Association)](https://github.com/OCA) ecosystem.

## License

Each package maintains its original license as specified in the OCA repositories.
