---
id: export-ebook
url: markdown/python-net/convert/export-ebook
title: Epub to Md
weight: 4
description: "This article demonstrates how to convert Ebook to Markdown with GroupDocs.Markdown for Python via .NET."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert EPUB, MOBI, and other eBook formats to clean Markdown.

### Using static method

The simplest way to convert an eBook file:

{{< tabs "export-ebook-static">}}
{{< tab "export_ebook_to_markdown.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter

def export_ebook_to_markdown():
    """Convert an EPUB eBook to Markdown using the static one-liner API."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Convert the EPUB directly to a Markdown file
    MarkdownConverter.to_file("business-plan.epub", "export-ebook-static.md")

if __name__ == "__main__":
    export_ebook_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQsAAABQCAYAAAAOa1DSAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAOxAAADsQBlSsOGwAAEHlJREFUeJzt3XlwG9d9wPHvLhYncRIA71sUKUqULFqHbR2xlUqx3dxOk0kzzbR2/2hnOnU7STr9r800f6SdTv9Ims60406OiXPUrq1YdeLEhyzLsiRKIi1SFy/xvm+QAHED/QMSKIgADSUZ05J+n7+0j2/3Pexb/bD78N4+ZbLvVBIhhPgAGkAymSQWSxCLx3PnVECv6dB0unRSPJ4gEo3l3EVVVYwGLb2dSCSJxuIkEonsRSgKek2HTqem02LxONFo7nrpdCoG/a1lJG6UkT0GKoqCXq9Dp66WEY3FicVyl6HpVPS3lBFPJIhG4yST2ctQVQW9pqGqCpDf+dU0HXrtTs6tgkGvoSirZURjceLx7OdW2k/a77dpv4
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_to_markdown/export-ebook-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-ebook-instance">}}
{{< tab "export_ebook_with_options.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def export_ebook_with_options():
    """Convert an EPUB eBook to Markdown using the instance API with image export and heading offset."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Open the eBook with a context manager
    with MarkdownConverter("business-plan.epub") as converter:
        # Step 3: Configure the image export strategy to save images to disk
        strategy = ExportImagesToFileSystemStrategy("images")
        strategy.images_relative_path = "images"

        # Step 4: Set conversion options
        options = ConvertOptions()
        options.image_export_strategy = strategy
        options.heading_level_offset = 1  # shift all headings down one level

        # Step 5: Convert and save the Markdown output
        converter.convert("export-ebook-instance.md", convert_options=options)

if __name__ == "__main__":
    export_ebook_with_options()
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-options.zip" >}}  
```text
export-ebook-instance.md (5 KB)
images/img-001.png (4 KB)
images/img-002.jpg (35 KB)
images/img-003.png (13 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_with_options/export-ebook-options.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
