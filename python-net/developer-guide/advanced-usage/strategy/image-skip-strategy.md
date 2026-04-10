---
id: image-skip-strategy
url: markdown/python-net/image-skip-strategy
title: Skip image
weight: 3
description: "The listed articles below explain how to skip saving images during document conversion."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use `SkipImagesStrategy` when you want to convert a document to Markdown without exporting any images. Image references will be omitted from the output.

### Using static method

{{< tabs "skip-images-static">}}
{{< tab "skip_images_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy

def skip_images_static():
    """Convert a PDF to Markdown while skipping all images."""

    # Step 1: Configure the skip-images strategy to omit images from output
    options = ConvertOptions()
    options.image_export_strategy = SkipImagesStrategy()

    # Step 2: Convert using keyword argument for options
    MarkdownConverter.to_file("business-plan.pdf", "skip-images-static.md", convert_options=options)

if __name__ == "__main__":
    skip_images_static()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "skip-images-static.txt" >}}  
```text
**HOME**** ****BASED**** ****PROFESSIONAL**** **

**SERVICES**** **

***Business****** ******Plan****** ***

**TABLE**** ****OF**** ****CONTENTS**** **

Introduction  3

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/skip_images_static/skip-images-static.txt)
{{< /tab >}}
{{< tab "skip-images-static.txt" >}}  
```text
**HOME BASED PROFESSIONAL SERVICES *Business Plan* TABLE OF CONTENTS** 

Introduction  3

1. Executive Summary  5
1. Company Overview  6
1. Business Description  7
1. Market Analysis  8
1. Operating Plan  10
1. Marketing and Sales Plan  11
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/skip_images_static/skip-images-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "skip-images-instance">}}
{{< tab "skip_images_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy

def skip_images_instance():
    """Skip all images during conversion using the instance API."""

    # Step 1: Configure the skip-images strategy
    options = ConvertOptions()
    options.image_export_strategy = SkipImagesStrategy()

    # Step 2: Open the document with a context manager
    with MarkdownConverter("business-plan.pdf") as converter:
        # Step 3: Convert using keyword argument for options
        converter.convert("skip-images-instance.md", convert_options=options)

if __name__ == "__main__":
    skip_images_instance()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "skip-images-instance.txt" >}}  
```text
**HOME**** ****BASED**** ****PROFESSIONAL**** **

**SERVICES**** **

***Business****** ******Plan****** ***

**TABLE**** ****OF**** ****CONTENTS**** **

Introduction  3

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/skip_images_instance/skip-images-instance.txt)
{{< /tab >}}
{{< tab "skip-images-instance.txt" >}}  
```text
**HOME BASED PROFESSIONAL SERVICES *Business Plan* TABLE OF CONTENTS** 

Introduction  3

1. Executive Summary  5
1. Company Overview  6
1. Business Description  7
1. Market Analysis  8
1. Operating Plan  10
1. Marketing and Sales Plan  11
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/skip_images_instance/skip-images-instance.txt)
{{< /tab >}}
{{< /tabs >}}
