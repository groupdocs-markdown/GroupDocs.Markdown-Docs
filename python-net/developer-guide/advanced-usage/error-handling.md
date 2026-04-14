---
id: error-handling
url: markdown/python-net/error-handling
title: Error handling
weight: 7
description: "Handle conversion errors with specific exception types"
keywords: error handling, exceptions, password, format, error
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

All conversion methods raise exceptions on failure. Use standard try/except with specific exception types:

{{< tabs "error-handling-example">}}
{{< tab "error_handling_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter
from groupdocs.markdown import DocumentProtectedException, InvalidFormatException, GroupDocsMarkdownException

def error_handling_example():
    """Demonstrate error handling with specific exception types during conversion."""

    try:
        # Step 1: Attempt to convert the document
        MarkdownConverter.to_file("annual-report.docx", "error-handling-example.md")
    except DocumentProtectedException:
        # Step 2a: Handle password-protected documents
        print("Wrong or missing password.")
    except InvalidFormatException:
        # Step 2b: Handle corrupt or unsupported file formats
        print("File is corrupt or unsupported.")
    except GroupDocsMarkdownException as ex:
        # Step 2c: Handle any other conversion errors
        print(f"Conversion failed: {ex}")

if __name__ == "__main__":
    error_handling_example()
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling-example.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/error_handling_example/error-handling-example.md)
{{< /tab >}}
{{< /tabs >}}

### Exception types

| Exception | When raised |
|---|---|
| `DocumentProtectedException` | Document is password-protected and no password or wrong password was provided |
| `InvalidFormatException` | File is corrupt or has an unrecognized format |
| `GroupDocsMarkdownException` | General conversion error |

### Conversion warnings

Non-fatal issues are reported via `ConvertResult.warnings`:

{{< tabs "warnings-example">}}
{{< tab "warnings_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def warnings_example():
    """Show how to inspect non-fatal conversion warnings after converting."""

    # Step 1: Open the spreadsheet with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 2: Configure row truncation
        options = ConvertOptions()
        options.max_rows = 10  # limit to first 10 data rows per sheet

        # Step 3: Convert and capture the result for inspection
        result = converter.convert("warnings-example.md", convert_options=options)

        # Step 4: Write any non-fatal warnings to a separate text file
        with open("warnings-example.txt", "w", encoding="utf-8") as f:
            for warning in result.warnings:
                f.write(f"Warning: {warning}\n")

if __name__ == "__main__":
    warnings_example()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "warnings-example.md" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/warnings_example/warnings-example.md)
{{< /tab >}}
{{< /tabs >}}
