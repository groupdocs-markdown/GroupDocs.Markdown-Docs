---
id: export-pdf
url: markdown/python-net/convert/export-pdf
title: Pdf to Md
weight: 1
description: "This article demonstrates how to convert PDF to Markdown with GroupDocs.Markdown for Python via .NET."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert PDF documents to clean Markdown.

### Using static method

The simplest way to convert a PDF file:

{{< tabs "export-pdf-static">}}
{{< tab "export_pdf_to_markdown.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter

def export_pdf_to_markdown():
    """Convert a PDF document to Markdown using the static one-liner API."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Convert PDF to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("business-plan.pdf")

    # Step 3: Or save the conversion result directly to a file
    MarkdownConverter.to_file("business-plan.pdf", "export-pdf.md")

if __name__ == "__main__":
    export_pdf_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_to_markdown/export-pdf.txt)
{{< /tab >}}
{{< tab "export-pdf.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_to_markdown/export-pdf.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-pdf-instance">}}
{{< tab "export_pdf_with_options.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def export_pdf_with_options():
    """Convert a PDF to Markdown using the instance API with image export and heading offset."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Open the PDF document with a context manager
    with MarkdownConverter("business-plan.pdf") as converter:
        # Step 3: Configure the image export strategy to save images to disk
        strategy = ExportImagesToFileSystemStrategy("images")
        strategy.images_relative_path = "images"

        # Step 4: Set conversion options
        options = ConvertOptions()
        options.image_export_strategy = strategy
        options.heading_level_offset = 1  # shift all headings down one level

        # Step 

        # Step 5: Convert and save the Markdown output
        converter.convert("export-pdf-options.md", convert_options=options)

if __name__ == "__main__":
    export_pdf_with_options()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-options.zip" >}}  
```text
export-pdf-options.txt (34 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_with_options/export-pdf-options.zip)
{{< /tab >}}
{{< tab "export-pdf-options.zip" >}}  
```text
export-pdf-options.txt (33 KB)
images/img-001.jpg (60 KB)
images/img-002.png (470 bytes)
images/img-003.png (2 KB)
images/img-004.jpg (56 KB)
images/img-005.png (330 bytes)
images/img-006.png (438 bytes)
images/img-007.png (438 bytes)
images/img-008.png (438 bytes)
images/img-009.png (438 bytes)
[TRUNCATED] (35 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_with_options/export-pdf-options.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
