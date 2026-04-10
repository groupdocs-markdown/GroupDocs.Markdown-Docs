---
id: load-from-a-local-disk
url: markdown/python-net/load-from-a-local-disk
title: Load from a local disk
weight: 1
description: "The following example demonstrates how to load file from local disk."
keywords: load file from local disk
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

GroupDocs.Markdown provides two ways to load a file from a local disk: the static one-liner API and the instance-based API.

### Using static method

The simplest approach -- pass a file path and get the Markdown string back:

{{< tabs "load-disk-static">}}
{{< tab "load_from_disk_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def load_from_disk_static():
    """Load and convert a local file to Markdown using the static API."""

    # Step 1: Convert a local file to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("business-plan.docx")

    # Step 2: Or save the result directly to a file on disk
    MarkdownConverter.to_file("business-plan.docx", "load-from-disk-static.md")

if __name__ == "__main__":
    load_from_disk_static()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-from-disk-static.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/load_from_disk_static/load-from-disk-static.txt)
{{< /tab >}}
{{< tab "load-from-disk-static.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/load_from_disk_static/load-from-disk-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

When you need more control (e.g., conversion options, document info), create a `MarkdownConverter` instance:

{{< tabs "load-disk-instance">}}
{{< tab "load_from_disk_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def load_from_disk_instance():
    """Load a local file with the instance API, inspect metadata, then convert."""

    # Step 1: Open the document with a context manager
    with MarkdownConverter("business-plan.docx") as converter:
        # Step 2: Retrieve document metadata before converting
        info = converter.get_document_info()
        print(f"Format: {info.file_format}, Pages: {info.page_count}")

        # Step 3: Convert to Markdown and print the result
        converter.convert("load-from-disk-instance.md")

if __name__ == "__main__":
    load_from_disk_instance()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-from-disk-instance.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/load_from_disk_instance/load-from-disk-instance.txt)
{{< /tab >}}
{{< tab "load-from-disk-instance.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/load_from_disk_instance/load-from-disk-instance.txt)
{{< /tab >}}
{{< /tabs >}}
