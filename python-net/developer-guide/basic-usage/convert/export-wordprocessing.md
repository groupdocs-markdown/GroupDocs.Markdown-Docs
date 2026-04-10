---
id: export-wordprocessing
url: markdown/python-net/convert/export-wordprocessing
title: Docx to Md
weight: 2
description: "This article demonstrates how to convert Words to Markdown with GroupDocs.Markdown for Python via .NET."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert DOCX and other Word documents to clean Markdown.

### Using static method

The simplest way to convert a Word file:

{{< tabs "export-word-static">}}
{{< tab "export_word_to_markdown.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter

def export_word_to_markdown():
    """Convert a Word document to Markdown using the static one-liner API."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Convert DOCX to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("business-plan.docx")

    # Step 3: Or save the conversion result directly to a file
    MarkdownConverter.to_file("business-plan.docx", "export-word.md")

if __name__ == "__main__":
    export_word_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/export_word_to_markdown/export-word.txt)
{{< /tab >}}
{{< tab "export-word.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/export_word_to_markdown/export-word.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-word-instance">}}
{{< tab "export_word_with_options.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def export_word_with_options():
    """Convert a Word document to Markdown using the instance API with image export and heading offset."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Open the DOCX document with a context manager
    with MarkdownConverter("business-plan.docx") as converter:
        # Step 3: Configure the image export strategy to save images to disk
        strategy = ExportImagesToFileSystemStrategy("images")
        strategy.images_relative_path = "images"

        # Step 4: Set conversion options
        options = ConvertOptions()
        options.image_export_strategy = strategy
        options.heading_level_offset = 1  # shift all headings down one level

        # Step 

        # Step 5: Convert and save the Markdown output
        converter.convert("export-word-options.md", convert_options=options)

if __name__ == "__main__":
    export_word_with_options()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word-options.zip" >}}  
```text
export-word-options.txt (21 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/export_word_with_options/export-word-options.zip)
{{< /tab >}}
{{< tab "export-word-options.zip" >}}  
```text
export-word-options.txt (20 KB)
images/img-001.jpg (56 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/export_word_with_options/export-word-options.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
