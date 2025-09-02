# PyPDF2 Compatibility Patch - Report QWeb Encrypt

## Overview

This patch addresses the PyPDF2 deprecation error in the report_qweb_encrypt module when using PyPDF2 version 3.0.0 or higher. The original error was:

```
PyPDF2.errors.DeprecationError: PdfFileWriter is deprecated and was removed in PyPDF2 3.0.0. Use PdfWriter instead.
```

## Problem

In PyPDF2 3.0.0, several classes and methods were deprecated and removed:
- `PdfFileWriter` → `PdfWriter`
- `PdfFileReader` → `PdfReader` 
- `appendPagesFromReader()` → `append_pages_from_reader()`

## Affected Functionality

The report_qweb_encrypt module uses PyPDF2 for:
- PDF encryption with password protection
- Appending pages from source PDF to encrypted output
- Secure report generation with user-defined passwords

## Solution

This patch provides backward compatibility by creating wrapper classes that:
1. Inherit from the new PyPDF2 classes (`PdfWriter`, `PdfReader`)
2. Provide the old method signatures as compatibility methods
3. Gracefully handle both old and new PyPDF2 versions

## Files Modified

### `report_qweb_encrypt/models/ir_actions_report.py`
- Added compatibility import logic
- Created local compatibility classes with required method aliases:
  - `PdfFileWriter.appendPagesFromReader()` → `PdfWriter.append_pages_from_reader()`

## Implementation Details

### Compatibility Import Pattern
```python
try:
    from PyPDF2 import PdfWriter, PdfReader
    
    # Create compatibility classes for PyPDF2 3.0+
    class PdfFileWriter(PdfWriter):
        def appendPagesFromReader(self, reader, after_page_append=None):
            return self.append_pages_from_reader(reader, after_page_append)
    
    class PdfFileReader(PdfReader):
        pass

except ImportError:
    # Fallback to old API for older PyPDF2 versions
    from PyPDF2 import PdfFileWriter, PdfFileReader
```

## Usage Example

The module allows encrypting reports with passwords:

```python
# In Odoo report configuration
report.qweb_pdf_encrypt = True
report.qweb_pdf_encrypt_password = "secret123"

# Generated PDF will be password-protected
```

## Testing

The patch has been tested with:
- PyPDF2 3.0.0+ (new API)
- PyPDF2 2.x (old API via fallback)
- PDF encryption functionality
- Password-protected report generation

## Branch Information

- **Branch**: `pdfwrite`
- **Based on**: Current master branch
- **Type**: Compatibility patch
- **Impact**: Backward compatible - no breaking changes

## Author

- **Developer**: Ernad Husremović (hernad@bring.out.ba)
- **Company**: bring.out.doo Sarajevo
- **Date**: 2025-09-02

## Related Issues

This patch resolves the PyPDF2 deprecation error encountered in:
- Password-protected PDF generation
- Report encryption workflows
- Secure document delivery

## Installation

This patch is automatically applied when using the `pdfwrite` branch. No additional installation steps required.

## Dependencies

- Works with encrypted PDF reports
- Maintains security functionality
- Compatible with existing password configurations

## Future Considerations

While this patch provides immediate compatibility, consider:
1. Eventually migrating to the new PyPDF2 API directly
2. Testing encryption with future PyPDF2 versions
3. Evaluating alternative PDF encryption libraries if needed