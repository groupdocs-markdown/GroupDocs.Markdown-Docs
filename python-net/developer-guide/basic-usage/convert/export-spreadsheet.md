---
id: export-spreadsheet
url: markdown/python-net/convert/export-spreadsheet
title: Xlsx to Md
weight: 3
description: "This article demonstrates how to convert Spreadsheet to Markdown with GroupDocs.Markdown for Python via .NET."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert XLSX and other spreadsheet files to Markdown tables. You can control how many columns and rows are included using spreadsheet-specific options.

### Using static method

The simplest way to convert a spreadsheet file:

{{< tabs "export-spreadsheet-static">}}
{{< tab "export_spreadsheet_to_markdown.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter

def export_spreadsheet_to_markdown():
    """Convert an Excel spreadsheet to Markdown using the static one-liner API."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Convert XLSX to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("cost-analysis.xlsx")

    # Step 3: Or save the conversion result directly to a file
    MarkdownConverter.to_file("cost-analysis.xlsx", "export-spreadsheet.md")

if __name__ == "__main__":
    export_spreadsheet_to_markdown()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/export_spreadsheet_to_markdown/export-spreadsheet.txt)
{{< /tab >}}
{{< tab "export-spreadsheet.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/export_spreadsheet_to_markdown/export-spreadsheet.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API. The `ConvertOptions` class provides spreadsheet-specific properties such as `max_columns` and `max_rows` to limit the size of the exported tables:

{{< tabs "export-spreadsheet-instance">}}
{{< tab "export_spreadsheet_with_options.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter, ConvertOptions

def export_spreadsheet_with_options():
    """Convert an Excel spreadsheet to Markdown with column/row limits and heading offset."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Open the spreadsheet with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 3: Configure spreadsheet-specific conversion options
        options = ConvertOptions()
        options.max_columns = 10   # limit to first 10 columns
        options.max_rows = 100     # limit to first 100 data rows per sheet
        options.heading_level_offset = 1  # shift headings down one level

        # Step 

        # Step 4: Convert and save the Markdown output
        converter.convert("export-spreadsheet-options.md", convert_options=options)

if __name__ == "__main__":
    export_spreadsheet_with_options()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet-options.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/export_spreadsheet_with_options/export-spreadsheet-options.txt)
{{< /tab >}}
{{< tab "export-spreadsheet-options.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/export_spreadsheet_with_options/export-spreadsheet-options.txt)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
