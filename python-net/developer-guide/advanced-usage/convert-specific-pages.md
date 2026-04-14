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
    MarkdownConverter.to_file("business-plan.docx", "convert-pages-static.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_static()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-pages-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_static/convert-pages-static.md)
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
        converter.convert("convert-pages-instance.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_instance()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-pages-instance.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_instance/convert-pages-instance.md)
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
    MarkdownConverter.to_file("business-plan.pdf", "convert-pages-to-file.md", convert_options=options)

if __name__ == "__main__":
    convert_specific_pages_to_file()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-pages-to-file.md" >}}  
```text
**Table of Contents**

Meridian Outdoor Co. — Business Plan .........................................................................................1FY2026 Strategic Plan.................................................................................................................1Table of Contents.............................................................................................................................2

1. Executive Summary..................................................
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/convert-specific-pages/convert_specific_pages_to_file/convert-pages-to-file.md)
{{< /tab >}}
{{< /tabs >}}
