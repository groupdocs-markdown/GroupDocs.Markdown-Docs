---
id: load-a-file-of-a-specific-format
url: markdown/python-net/load-a-file-of-a-specific-format
title: Load a file of a specific format
weight: 3
description: "This example demonstrates how to load a file of some particular format."
keywords: load a file
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

By default, GroupDocs.Markdown detects the file format automatically from the file extension or stream content. When you want to skip auto-detection or the file extension is missing, specify the format explicitly using `LoadOptions`.

{{< tabs "load-specific-format">}}
{{< tab "load_specific_format.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, LoadOptions, FileFormat

def load_specific_format():
    """Load a file with an explicitly specified format, skipping auto-detection."""

    # Step 1: Create load options with the explicit file format
    load_options = LoadOptions(FileFormat.XLSX)

    # Step 2: Open the file with load options using keyword argument
    with MarkdownConverter("cost-analysis.xlsx", load_options=load_options) as converter:
        # Step 3: Convert and save the Markdown output
        converter.convert("load-specific-format.md")

if __name__ == "__main__":
    load_specific_format()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-specific-format.md" >}}  
```text
## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
| Parts and materials | $1,325,000.00 | $1,480,000.00 | $1,620,000.00 |
| Manufacturing equipment | $900,500.00 | $980,000.00 | $1,050,000.00 |
| Warehousing | $420,000.00 | $510,000.00 | $590,000.00 |
| Shipping | $380,000.00 | $445,000.00 | $520,000.00 |
| Marketing | $250,000.00 | $340,000.00 | $480,000.00 |
| R&D | $180,000.00 | $230,000.00 | $310,000.00 |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-file-of-a-specific-format/load_specific_format/load-specific-format.md)
{{< /tab >}}
{{< /tabs >}}

### Available FileFormat values

The `FileFormat` enum includes the following values:

| Category | Values |
|---|---|
| Word Processing | `DOC`, `DOCX`, `DOCM`, `DOT`, `DOTX`, `DOTM`, `RTF`, `ODT`, `OTT` |
| Spreadsheet | `XLSX`, `XLS`, `XLSB`, `XLSM`, `CSV`, `TSV`, `ODS`, `OTS` |
| PDF | `PDF` |
| E-book | `EPUB`, `MOBI` |
| Text | `TXT` |
| Help | `CHM` |

You can also retrieve supported formats programmatically:

{{< tabs "get-supported-formats">}}
{{< tab "get_supported_formats.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def get_supported_formats():
    """List all file formats supported by GroupDocs.Markdown."""

    # Step 1: Retrieve the list of supported formats
    formats = MarkdownConverter.get_supported_formats()

    # Step 2: Print each supported format
    for fmt in formats:
        print(fmt)

if __name__ == "__main__":
    get_supported_formats()
```
{{< /tab >}}
{{< /tabs >}}
