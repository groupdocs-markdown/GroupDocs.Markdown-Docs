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

    # Step 2: Convert the PDF directly to a Markdown file
    MarkdownConverter.to_file("business-plan.pdf", "export-pdf-static.md")

if __name__ == "__main__":
    export_pdf_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAIAAADHHcVbAAAAA3NCSVQICAjb4U/gAAAMWElEQVR4nO3dUWzV130H8L+nSnsgxYTa5kbEnhJgJpJ98aQseTAxUaoiW1RDSiseykoCNE9boyoIZEWLVImosoZSpeve0Ighax4iDRRpky02oWKbh2aVCralhGBANSAu4Lq5NJ60tz0c8t/lf6/h2jjg/M/nIz8c7v/v3z345atz/v9zTkNpaiwBgFj92aPuAAA8SoIQgKgJQgCiJggBiNo3Mv/+53/9r4tXbi6u1t/v/Pa6tjXzXV1cZTXVVFNNNdVc2poZ2SCcmr4xfv7KQr8y+NPc/97j6uIqq6mmmmqqqebS1szIBuH6tjUNDQ0Xp2988T8LqAIAX1NLOSIEgK+dhsyC+p/87FdpEP7dzm+va613jjVJkvVtax5b8efzXb04fWNBY1U11VRTTTXVXJ
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_to_markdown/export-pdf-static.md)
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

        # Step 5: Convert and save the Markdown output
        converter.convert("export-pdf-instance.md", convert_options=options)

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
export-pdf-instance.md (7 KB)
images/img-001.png (3 KB)
images/img-002.jpg (73 KB)
images/img-003.jpg (76 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-pdf/export_pdf_with_options/export-pdf-options.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
