---
id: heading-offset
url: markdown/python-net/heading-offset
title: Heading level offset
weight: 5
description: "Shift all heading levels in the Markdown output"
keywords: heading, offset, heading level, embed
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Use `heading_level_offset` to shift all heading levels in the output by a fixed number. This is useful when embedding converted content inside a larger document where top-level headings are already in use.

### Example

{{< tabs "heading-offset-example">}}
{{< tab "heading_offset_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def heading_offset_example():
    """Shift all heading levels by a fixed offset when converting to Markdown."""

    # Step 1: Set the heading level offset to 2
    options = ConvertOptions()
    options.heading_level_offset = 2  # shift all headings down two levels

    # Step 2: Convert the document using keyword argument for options
    md = MarkdownConverter.to_markdown("annual-report.docx", convert_options=options)

    # Source: # Title     -> Output: ### Title
    # Source: ## Section  -> Output: #### Section
    # Heading levels are clamped to the range 1-6.

if __name__ == "__main__":
    heading_offset_example()
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}
