# PyPDF2 Compatibility Patch - Report QWeb PDF Cover

## Overview

This patch addresses the PyPDF2 deprecation error in the report_qweb_pdf_cover module when using PyPDF2 version 3.0.0 or higher. The original error was:

```
PyPDF2.errors.DeprecationError: PdfFileWriter is deprecated and was removed in PyPDF2 3.0.0. Use PdfWriter instead.
```

## Problem

In PyPDF2 3.0.0, several classes and methods were deprecated and removed:
- `PdfFileWriter` → `PdfWriter`
- `PdfFileReader` → `PdfReader` 

## Affected Functionality

The report_qweb_pdf_cover module uses PyPDF2 for:
- Adding front and back covers to PDF reports
- PDF page manipulation and insertion
- Cover page validation and processing
- Comprehensive report formatting with covers

## Solution

This patch provides backward compatibility by creating a simple import compatibility layer that:
1. Attempts to import from the new PyPDF2 API (`PdfWriter`, `PdfReader`)
2. Falls back to the old API for older PyPDF2 versions
3. Maintains full functionality without code changes

## Files Modified

### `report_qweb_pdf_cover/models/ir_actions_report.py`
- Added compatibility import logic for basic PyPDF2 class imports
- Maintains existing functionality without method wrapper requirements

## Implementation Details

### Compatibility Import Pattern
```python
try:
    from PyPDF2 import PdfWriter as PdfFileWriter, PdfReader as PdfFileReader
except ImportError:
    # Fallback to old API for older PyPDF2 versions
    from PyPDF2 import PdfFileWriter, PdfFileReader
```

## Usage Example

The module allows adding covers to reports:

```python
# In Odoo report configuration
report.pdf_front_cover = base64_encoded_pdf_cover
report.pdf_back_cover = base64_encoded_pdf_cover

# Generated report will include covers
```

## Functionality Features

- **Front Cover Support**: Add custom front covers to reports
- **Back Cover Support**: Add custom back covers to reports  
- **Cover Validation**: Validates PDF cover files before processing
- **Page Management**: Handles complex page insertion logic
- **Error Handling**: Graceful degradation when covers are invalid

## Testing

The patch has been tested with:
- PyPDF2 3.0.0+ (new API)
- PyPDF2 2.x (old API via fallback)
- Front cover attachment
- Back cover attachment
- Cover validation workflows

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
- PDF cover page insertion
- Report formatting with covers
- Custom branded document generation

## Installation

This patch is automatically applied when using the `pdfwrite` branch. No additional installation steps required.

## Dependencies

- Compatible with custom PDF covers
- Maintains cover validation functionality
- Works with existing cover configuration

## Future Considerations

While this patch provides immediate compatibility, consider:
1. Eventually migrating to the new PyPDF2 API directly
2. Testing cover functionality with future PyPDF2 versions
3. Enhancing cover validation and error handling