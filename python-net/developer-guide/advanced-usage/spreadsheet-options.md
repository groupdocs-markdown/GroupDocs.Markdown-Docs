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

    # Step 2: Convert with truncation options using keyword argument
    md = MarkdownConverter.to_markdown("cost-analysis.xlsx", convert_options=options)

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
        # Step 3: Convert using keyword argument for options
        result = converter.convert(convert_options=options)

        # Step 4: Check for conversion warnings (e.g., truncation)
        for warning in result.warnings:
            print(f"Warning: {warning}")
        # e.g. "Worksheet 'Data' truncated at 50 rows."

if __name__ == "__main__":
    spreadsheet_sheets()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Available options

| Property | Type | Default | Description |
|---|---|---|---|
| `max_columns` | `int` | `0` (unlimited) | Maximum columns per table |
| `max_rows` | `int` | `0` (unlimited) | Maximum data rows per worksheet |
| `sheet_separator` | `str` | `"\n---\n"` | Separator inserted between worksheets |
| `include_hidden_sheets` | `bool` | `False` | Whether to include hidden worksheets |
