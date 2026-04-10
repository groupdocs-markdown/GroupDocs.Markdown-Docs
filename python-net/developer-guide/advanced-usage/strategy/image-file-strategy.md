---
id: image-file-strategy
url: markdown/python-net/image-file-strategy
title: Save image as file
weight: 2
description: "The listed articles below explain how to save images to the file system during document conversion."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use `ExportImagesToFileSystemStrategy` to save images as separate files during conversion. The Markdown output will contain image references pointing to the exported files.

### Basic usage

{{< tabs "image-file-basic">}}
{{< tab "image_file_basic.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def image_file_basic():
    """Save images to a folder on disk during PDF to Markdown conversion."""

    # Step 1: Configure the file system image export strategy
    options = ConvertOptions()
    options.image_export_strategy = ExportImagesToFileSystemStrategy("output/images")

    # Step 2: Convert and save to file using keyword argument for options
    MarkdownConverter.to_file("business-plan.pdf", "output/document.md", convert_options=options)

if __name__ == "__main__":
    import os
    os.makedirs("output/images", exist_ok=True)
    image_file_basic()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-basic.zip" >}}  
```text
output/document.txt (34 KB)
output/images/img-001.jpg (60 KB)
output/images/img-002.png (470 bytes)
output/images/img-003.png (2 KB)
output/images/img-004.jpg (56 KB)
output/images/img-005.png (330 bytes)
output/images/img-006.png (438 bytes)
output/images/img-007.png (438 bytes)
output/images/img-008.png (438 bytes)
output/images/img-009.png (438 bytes)
... (35 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/image_file_basic/image-file-basic.zip)
{{< /tab >}}
{{< tab "image-file-basic.zip" >}}  
```text
output/document.txt (33 KB)
output/images/img-001.jpg (60 KB)
output/images/img-002.png (470 bytes)
output/images/img-003.png (2 KB)
output/images/img-004.jpg (56 KB)
output/images/img-005.png (330 bytes)
output/images/img-006.png (438 bytes)
output/images/img-007.png (438 bytes)
output/images/img-008.png (438 bytes)
output/images/img-009.png (438 bytes)
[TRUNCATED] (35 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/image_file_basic/image-file-basic.zip)
{{< /tab >}}
{{< /tabs >}}

### Using images_relative_path

By default, image references in the Markdown use the full images folder path. Set `images_relative_path` to produce portable, relative image links:

{{< tabs "image-file-relative">}}
{{< tab "image_file_relative.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def image_file_relative():
    """Save images to disk with portable, relative paths in the Markdown output."""

    # Step 1: Configure the image export strategy with a relative path
    strategy = ExportImagesToFileSystemStrategy("output/images")
    strategy.images_relative_path = "images"  # produces ![](images/img-001.png)

    # Step 2: Assign the strategy to conversion options
    options = ConvertOptions()
    options.image_export_strategy = strategy

    # Step 3: Convert and save using keyword argument for options
    MarkdownConverter.to_file("business-plan.pdf", "output/document.md", convert_options=options)

    # Markdown output contains: ![](images/img-001.png)
    # Image file saved to:     output/images/img-001.png

if __name__ == "__main__":
    import os
    os.makedirs("output/images", exist_ok=True)
    image_file_relative()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-relative.zip" >}}  
```text
output/document.txt (34 KB)
output/images/img-001.jpg (60 KB)
output/images/img-002.png (470 bytes)
output/images/img-003.png (2 KB)
output/images/img-004.jpg (56 KB)
output/images/img-005.png (330 bytes)
output/images/img-006.png (438 bytes)
output/images/img-007.png (438 bytes)
output/images/img-008.png (438 bytes)
output/images/img-009.png (438 bytes)
... (35 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/image_file_relative/image-file-relative.zip)
{{< /tab >}}
{{< tab "image-file-relative.zip" >}}  
```text
output/document.txt (33 KB)
output/images/img-001.jpg (60 KB)
output/images/img-002.png (470 bytes)
output/images/img-003.png (2 KB)
output/images/img-004.jpg (56 KB)
output/images/img-005.png (330 bytes)
output/images/img-006.png (438 bytes)
output/images/img-007.png (438 bytes)
output/images/img-008.png (438 bytes)
output/images/img-009.png (438 bytes)
[TRUNCATED] (35 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/image_file_relative/image-file-relative.zip)
{{< /tab >}}
{{< /tabs >}}
