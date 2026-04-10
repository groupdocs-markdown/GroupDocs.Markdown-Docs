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

    # Step 2: Convert EPUB to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("business-plan.epub")

    # Step 3: Or save the conversion result directly to a file
    MarkdownConverter.to_file("business-plan.epub", "export-ebook.md")

if __name__ == "__main__":
    export_ebook_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook.txt" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUoAAAAICAYAAACfzrbWAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEwAACxMBAJqcGAAAAIdJREFUaIHt1KENAkEQRuE3yyVYekHhthQ6wV8TUAod0AECT3AYkh0sF8Q6DsL75CST/OrF7bSvtFJ5ERHLzNwgSf8iuJCcp6e8r9bbcaCVGrCbPGQSH10oSTNr8Ba+jCswlhnmSNJPMZSS1GEoJanDUEpSh6GUpI6B0g4Jx7mHSNK3WRAPgCfpERinQ8MkdQAAAABJRU5ErkJggg==)HOME BASED  

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOcAAABFCAYAAACxIPHFAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEwAACxMBAJqcGAAAASxJREFUeJzt1bFRAlEARdH/EXNLo
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_to_markdown/export-ebook.txt)
{{< /tab >}}
{{< tab "export-ebook.txt" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUoAAAAICAYAAACfzrbWAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEwAACxMBAJqcGAAAAIdJREFUaIHt1KENAkEQRuE3yyVYekHhthQ6wV8TUAod0AECT3AYkh0sF8Q6DsL75CST/OrF7bSvtFJ5ERHLzNwgSf8iuJCcp6e8r9bbcaCVGrCbPGQSH10oSTNr8Ba+jCswlhnmSNJPMZSS1GEoJanDUEpSh6GUpI6B0g4Jx7mHSNK3WRAPgCfpERinQ8MkdQAAAABJRU5ErkJggg==)HOME BASED  

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOcAAABFCAYAAACxIPHFAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEwAACxMBAJqcGAAAASxJREFUeJzt1bFRAlEARdH/EXNLo
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_to_markdown/export-ebook.txt)
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

        # Step 

        # Step 5: Convert and save the Markdown output
        converter.convert("export-ebook-options.md", convert_options=options)

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
export-ebook-options.txt (44 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_with_options/export-ebook-options.zip)
{{< /tab >}}
{{< tab "export-ebook-options.zip" >}}  
```text
export-ebook-options.txt (44 KB)
images/img-001.png (229 bytes)
images/img-002.png (394 bytes)
images/img-003.png (8 KB)
images/img-004.png (171 bytes)
images/img-005.png (9 KB)
images/img-006.png (567 bytes)
images/img-007.png (151 bytes)
images/img-008.png (186 bytes)
images/img-009.png (567 bytes)
[TRUNCATED] (610 files total)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-ebook/export_ebook_with_options/export-ebook-options.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
