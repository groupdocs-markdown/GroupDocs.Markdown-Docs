---
id: convert-specific-pages
url: markdown/python-net/convert-specific-pages
title: Convert specific pages
weight: 4
description: "This article demonstrates how to convert specific document pages by page number using GroupDocs.Markdown for Python via .NET API."
keywords: Convert page, Convert pages, Convert specific pages
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use the `page_numbers` property of `ConvertOptions` to convert only selected pages (or worksheets) from the source document. Page numbering starts from 1.

### Using static method

{{< tabs "convert-pages-static">}}
{{< tab "convert_specific_pages_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def convert_specific_pages_static():
    """Convert only specific pages from a document using the static API."""

    # Step 1: Specify which pages to convert (1-based numbering)
    options = ConvertOptions()
    options.page_numbers = [1, 3]  # convert only pages 1 and 3

    # Step 2: Convert selected pages using keyword argument for options
    MarkdownConverter.to_file("business-plan.docx", "convert-specific-pages-static.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_static()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-specific-pages-static.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



| Introduction |
| --- |
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_static/convert-specific-pages-static.txt)
{{< /tab >}}
{{< tab "convert-specific-pages-static.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_static/convert-specific-pages-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "convert-pages-instance">}}
{{< tab "convert_specific_pages_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def convert_specific_pages_instance():
    """Convert only specific pages from a document using the instance API."""

    # Step 1: Open the document with a context manager
    with MarkdownConverter("business-plan.docx") as converter:
        # Step 2: Specify which pages to convert (1-based numbering)
        options = ConvertOptions()
        options.page_numbers = [1, 3]  # convert only pages 1 and 3

        # Step 3: Convert and save the result
        converter.convert("convert-specific-pages-instance.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_instance()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-specific-pages-instance.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



| Introduction |
| --- |
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_instance/convert-specific-pages-instance.txt)
{{< /tab >}}
{{< tab "convert-specific-pages-instance.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_instance/convert-specific-pages-instance.txt)
{{< /tab >}}
{{< /tabs >}}

### Save specific pages to a file

{{< tabs "convert-pages-to-file">}}
{{< tab "convert_specific_pages_to_file.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def convert_specific_pages_to_file():
    """Convert specific pages from a PDF and save the result to a file."""

    # Step 1: Specify which pages to convert (1-based numbering)
    options = ConvertOptions()
    options.page_numbers = [2, 4, 5]  # convert pages 2, 4, and 5

    # Step 2: Convert and save to file using keyword argument for options
    MarkdownConverter.to_file("business-plan.pdf", "convert-specific-pages.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_to_file()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-specific-pages.txt" >}}  
```text
**TABLE**** ****OF**** ****CONTENTS**** **![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAOhAVcDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAAAAQFBgcIAwEJAv/EAGYQAAACBAoHBQUEBAoGBQsBCQMEAAEFEQYTFCExQVFhgfAkcZGhscHhBxUjNNElM0RU8RY1Q2QCRXSCCBJSU1VjZXWEoiZChZTC4jI2laXFFyJGVnJzkqS0tdLWJzdidobV5Ob0/8QAGwEBAQEAAwE
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_to_file/convert-specific-pages.txt)
{{< /tab >}}
{{< tab "convert-specific-pages.txt" >}}  
```text
**TABLE OF CONTENTS** ![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAOhAVcDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAAAAQFBgcIAwEJAv/EAGYQAAACBAoHBQUEBAoGBQsBCQMEAAEFEQYTFCExQVFhgfAkcZGhscHhBxUjNNElM0RU8RY1Q2QCRXSCCBJSU1VjZXWEoiZChZTC4jI2laXFFyJGVnJzkqS0tdLWJzdidobV5Ob0/8QAGwEBAQEAAwEBAAAAAAAAAAAAAAQFAQM
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_to_file/convert-specific-pages.txt)
{{< /tab >}}
{{< /tabs >}}
