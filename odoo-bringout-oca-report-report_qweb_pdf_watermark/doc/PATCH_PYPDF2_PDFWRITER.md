# PyPDF2 Compatibility Patch - Report QWeb PDF Watermark

## Overview

This patch addresses the PyPDF2 deprecation error in the report_qweb_pdf_watermark module when using PyPDF2 version 3.0.0 or higher. The original errors were:

```
PyPDF2.errors.DeprecationError: PdfFileWriter is deprecated and was removed in PyPDF2 3.0.0. Use PdfWriter instead.
PyPDF2.errors.DeprecationError: addBlankPage is deprecated and was removed in PyPDF2 3.0.0. Use add_blank_page instead.
```

## Problem

In PyPDF2 3.0.0, several classes and methods were deprecated and removed:
- `PdfFileWriter` → `PdfWriter`
- `PdfFileReader` → `PdfReader` 
- `addBlankPage()` → `add_blank_page()`
- `PyPDF2.utils.PdfReadError` → `PyPDF2.errors.PdfReadError`

## Affected Functionality

The report_qweb_pdf_watermark module uses PyPDF2 for:
- Adding watermarks to PDF reports
- Creating blank pages with specific dimensions
- PDF page manipulation and processing
- Error handling for corrupted PDF files

## Solution

This patch provides backward compatibility by creating wrapper classes that:
1. Inherit from the new PyPDF2 classes (`PdfWriter`, `PdfReader`)
2. Provide the old method signatures as compatibility methods
3. Handle import location changes for exception classes
4. Gracefully handle both old and new PyPDF2 versions

## Files Modified

### `report_qweb_pdf_watermark/models/report.py`
- Added compatibility import logic
- Created local compatibility classes with required method aliases:
  - `PdfFileWriter.addBlankPage()` → `PdfWriter.add_blank_page()`
- Updated exception import: `PyPDF2.utils.PdfReadError` → `PyPDF2.errors.PdfReadError`

## Implementation Details

### Compatibility Import Pattern
```python
try:
    from PyPDF2 import PdfWriter, PdfReader
    from PyPDF2.errors import PdfReadError
    
    # Create compatibility classes for PyPDF2 3.0+
    class PdfFileWriter(PdfWriter):
        def addBlankPage(self, width=None, height=None):
            return self.add_blank_page(width, height)
    
    class PdfFileReader(PdfReader):
        pass

except ImportError:
    try:
        from PyPDF2 import PdfFileWriter, PdfFileReader
        from PyPDF2.utils import PdfReadError
    except ImportError:
        logger.debug("Can not import PyPDF2")
```

## Testing

The patch has been tested with:
- PyPDF2 3.0.0+ (new API)
- PyPDF2 2.x (old API via fallback)
- PDF watermark application
- Blank page creation
- Error handling for invalid PDFs

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
- PDF watermark application
- Report post-processing with watermarks
- Custom PDF page manipulation

## Installation

This patch is automatically applied when using the `pdfwrite` branch. No additional installation steps required.

## Future Considerations

While this patch provides immediate compatibility, consider:
1. Eventually migrating to the new PyPDF2 API directly
2. Testing watermark functionality with future PyPDF2 versions
3. Evaluating alternative PDF manipulation libraries if needed