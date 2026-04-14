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

    # Step 2: Write the metadata fields to a text file
    with open("get-info-static.txt", "w", encoding="utf-8") as f:
        f.write(f"Format:    {info.file_format}\n")     # Docx
        f.write(f"Pages:     {info.page_count}\n")      # 42
        f.write(f"Title:     {info.title}\n")           # "Q3 Report"
        f.write(f"Author:    {info.author}\n")          # "Jane Doe"
        f.write(f"Encrypted: {info.is_encrypted}\n")    # False

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
Pages:     5
Title:     Meridian Outdoor Co. — Business Plan
Author:    Meridian Outdoor Co.
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

        # Step 3: Write the metadata fields to a text file
        with open("get-info-instance.txt", "w", encoding="utf-8") as f:
            f.write(f"Format:    {info.file_format}\n")
            f.write(f"Pages:     {info.page_count}\n")
            f.write(f"Title:     {info.title}\n")
            f.write(f"Author:    {info.author}\n")
            f.write(f"Encrypted: {info.is_encrypted}\n")

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
Format:    Xlsx
Pages:     4
Title:     
Author:    
Encrypted: False
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
