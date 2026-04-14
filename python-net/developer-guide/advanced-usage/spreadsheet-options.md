---
id: spreadsheet-options
url: markdown/python-net/spreadsheet-options
title: Spreadsheet conversion options
weight: 6
description: "Control column truncation, row limits, sheet separators, and hidden worksheets"
keywords: spreadsheet, Excel, CSV, columns, rows, truncation, worksheets
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

When converting spreadsheets, use these properties on `ConvertOptions` to control the Markdown table output.

### Column and row truncation

{{< tabs "spreadsheet-truncation">}}
{{< tab "spreadsheet_truncation.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def spreadsheet_truncation():
    """Convert a spreadsheet with column and row truncation limits."""

    # Step 1: Configure column and row limits
    options = ConvertOptions()
    options.max_columns = 8     # only include the first 8 columns
    options.max_rows = 50       # only include the first 50 data rows per sheet

    # Step 2: Convert with truncation options and save to a file
    MarkdownConverter.to_file("cost-analysis.xlsx", "spreadsheet-truncation.md", convert_options=options)

    # Truncated columns/rows show "..." indicators.
    # Warnings are reported in ConvertResult.warnings.

if __name__ == "__main__":
    spreadsheet_truncation()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "spreadsheet-truncation.md" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/spreadsheet-options/spreadsheet_truncation/spreadsheet-truncation.md)
{{< /tab >}}
{{< /tabs >}}

### Sheet separator and hidden sheets

{{< tabs "spreadsheet-sheets">}}
{{< tab "spreadsheet_sheets.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def spreadsheet_sheets():
    """Convert a workbook with custom sheet separators and hidden sheet filtering."""

    # Step 1: Configure sheet separator and hidden sheet behavior
    options = ConvertOptions()
    options.sheet_separator = "\n---\n"      # horizontal rule between worksheets
    options.include_hidden_sheets = False    # skip hidden worksheets (default)

    # Step 2: Open the workbook with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 3: Convert and save the Markdown output
        converter.convert("spreadsheet-sheets.md", convert_options=options)

if __name__ == "__main__":
    spreadsheet_sheets()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "spreadsheet-sheets.md" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/spreadsheet-options/spreadsheet_sheets/spreadsheet-sheets.md)
{{< /tab >}}
{{< /tabs >}}

### Available options

| Property | Type | Default | Description |
|---|---|---|---|
| `max_columns` | `int` | `0` (unlimited) | Maximum columns per table |
| `max_rows` | `int` | `0` (unlimited) | Maximum data rows per worksheet |
| `sheet_separator` | `str` | `"\n---\n"` | Separator inserted between worksheets |
| `include_hidden_sheets` | `bool` | `False` | Whether to include hidden worksheets |
