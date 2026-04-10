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
{{< tab "load-specific-format.txt" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-file-of-a-specific-format/load_specific_format/load-specific-format.txt)
{{< /tab >}}
{{< tab "load-specific-format.txt" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-file-of-a-specific-format/load_specific_format/load-specific-format.txt)
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
