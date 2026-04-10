---
id: get-document-info
url: markdown/python-net/get-document-info
title: Get document info
weight: 2
description: "Retrieve document metadata such as format, page count, title, and author without converting"
keywords: document info, metadata, page count, file format
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Use `get_document_info()` or the static `get_info()` method to retrieve document metadata without performing a full conversion. This is useful for building file browsers, validation pipelines, and pre-conversion UIs.

### Using static method

{{< tabs "get-info-static">}}
{{< tab "get_info_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def get_info_static():
    """Retrieve document metadata using the static GetInfo method."""

    # Step 1: Get document info without performing a full conversion
    info = MarkdownConverter.get_info("business-plan.docx")

    # Step 2: Print the metadata fields
    print(f"Format:    {info.file_format}")     # Docx
    print(f"Pages:     {info.page_count}")      # 42
    print(f"Title:     {info.title}")            # "Q3 Report"
    print(f"Author:    {info.author}")           # "Jane Doe"
    print(f"Encrypted: {info.is_encrypted}")     # False

if __name__ == "__main__":
    get_info_static()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-static.txt" >}}  
```text
Format:    Docx
Pages:     18
Title:     
Author:    
Encrypted: False
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/get-document-info/get_info_static/get-info-static.txt)
{{< /tab >}}
{{< tab "get-info-static.txt" >}}  
```text
Format:    Docx
Pages:     18
Title:     
Author:    
Encrypted: False
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/get-document-info/get_info_static/get-info-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance method

{{< tabs "get-info-instance">}}
{{< tab "get_info_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def get_info_instance():
    """Retrieve document metadata using the instance API."""

    # Step 1: Open the spreadsheet with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 2: Retrieve document metadata
        info = converter.get_document_info()

        print(f"Format:     {info.file_format}")
        print(f"Pages:      {info.page_count}")
        print(f"Title:      {info.title}")
        print(f"Author:     {info.author}")
        print(f"Encrypted:  {info.is_encrypted}")

if __name__ == "__main__":
    get_info_instance()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-instance.txt" >}}  
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
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/get-document-info/get_info_instance/get-info-instance.txt)
{{< /tab >}}
{{< tab "get-info-instance.txt" >}}  
```text
Format:     Xlsx
Pages:      1
Title:      Cost Analysis
Author:     GroupDocs
Encrypted:  False
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/get-document-info/get_info_instance/get-info-instance.txt)
{{< /tab >}}
{{< /tabs >}}

### DocumentInfo properties

| Property | Type | Description |
|---|---|---|
| `file_format` | `FileFormat` | Detected file format (e.g., `FileFormat.DOCX`) |
| `page_count` | `int` | Number of pages or worksheets |
| `title` | `str` | Document title from metadata |
| `author` | `str` | Document author from metadata |
| `is_encrypted` | `bool` | Whether the document is password-protected |
