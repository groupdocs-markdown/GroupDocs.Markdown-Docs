---
id: export-text
url: markdown/python-net/convert/export-text
title: Xml to Md
weight: 5
description: "This article demonstrates how to convert Text to Markdown with GroupDocs.Markdown for Python via .NET."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert TXT, XML, and other text-based formats to clean Markdown.

### Using static method

The simplest way to convert a text file:

{{< tabs "export-text-static">}}
{{< tab "export_text_to_markdown.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter

def export_text_to_markdown():
    """Convert an XML/text file to Markdown using the static one-liner API."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Convert XML to a Markdown string in one call
    markdown = MarkdownConverter.to_markdown("llms-tech.xml")

    # Step 3: Or save the conversion result directly to a file
    MarkdownConverter.to_file("llms-tech.xml", "export-text.md")

if __name__ == "__main__":
    export_text_to_markdown()
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text.txt" >}}  
```text
`<Technologies>`

`<Category name="Model Architectures">`

`<Technology>`

`<Name>Transformer</Name>`

`<Description>Attention-based neural architecture used by most modern LLMs.</Description>`

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-text/export_text_to_markdown/export-text.txt)
{{< /tab >}}
{{< tab "export-text.txt" >}}  
```text
`<Technologies>`

`<Category name="Model Architectures">`

`<Technology>`

`<Name>Transformer</Name>`

`<Description>Attention-based neural architecture used by most modern LLMs.</Description>`

[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-text/export_text_to_markdown/export-text.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-text-instance">}}
{{< tab "export_text_with_options.py" >}}  
```python
import os
from groupdocs.markdown import License, MarkdownConverter, ConvertOptions

def export_text_with_options():
    """Convert an XML/text file to Markdown using the instance API with heading offset."""

    # Step 1: Apply the license (optional for evaluation)
    if os.path.exists("GroupDocs.Markdown.lic"):
        License.set_("GroupDocs.Markdown.lic")

    # Step 2: Open the text file with a context manager
    with MarkdownConverter("llms-tech.xml") as converter:
        # Step 3: Configure conversion options
        options = ConvertOptions()
        options.heading_level_offset = 1  # shift all headings down one level

        # Step 

        # Step 4: Convert and save the Markdown output
        converter.convert("export-text-options.md", convert_options=options)

if __name__ == "__main__":
    export_text_with_options()
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text-options.txt" >}}  
```text
`<Technologies>`

`<Category name="Model Architectures">`

`<Technology>`

`<Name>Transformer</Name>`

`<Description>Attention-based neural architecture used by most modern LLMs.</Description>`

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-text/export_text_with_options/export-text-options.txt)
{{< /tab >}}
{{< tab "export-text-options.txt" >}}  
```text
`<Technologies>`

`<Category name="Model Architectures">`

`<Technology>`

`<Name>Transformer</Name>`

`<Description>Attention-based neural architecture used by most modern LLMs.</Description>`

[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/export-text/export_text_with_options/export-text-options.txt)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/python-net/getting-started/supported-document-formats" >}}).
