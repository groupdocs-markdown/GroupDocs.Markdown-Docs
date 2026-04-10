---
id: markdown-flavor
url: markdown/python-net/markdown-flavor
title: Markdown flavor control
weight: 3
description: "Target GitHub Flavored Markdown or CommonMark output"
keywords: markdown flavor, GFM, CommonMark, tables
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

GroupDocs.Markdown supports two Markdown dialects. Set the `flavor` property on `ConvertOptions` to control the output.

### GitHub Flavored Markdown (default)

GFM supports pipe tables, strikethrough text, and other extensions:

{{< tabs "flavor-github">}}
{{< tab "flavor_github.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, MarkdownFlavor

def flavor_github():
    """Convert a document to GitHub Flavored Markdown with pipe tables and strikethrough."""

    # Step 1: Set the Markdown flavor to GitHub (GFM)
    options = ConvertOptions()
    options.flavor = MarkdownFlavor.GIT_HUB

    # Step 2: Convert the document using keyword argument for options
    md = MarkdownConverter.to_markdown("business-plan.docx", convert_options=options)

    # Tables are rendered as:
    # | Column A | Column B |
    # | --- | --- |
    # | value1 | value2 |

if __name__ == "__main__":
    flavor_github()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### CommonMark

Strict CommonMark output. Tables are rendered as fenced code blocks since CommonMark has no native table syntax:

{{< tabs "flavor-commonmark">}}
{{< tab "flavor_commonmark.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, MarkdownFlavor

def flavor_commonmark():
    """Convert a document to strict CommonMark format (no table extensions)."""

    # Step 1: Set the Markdown flavor to CommonMark
    options = ConvertOptions()
    options.flavor = MarkdownFlavor.COMMON_MARK

    # Step 2: Convert the document using keyword argument for options
    md = MarkdownConverter.to_markdown("business-plan.docx", convert_options=options)

    # Tables are rendered as fenced code blocks since CommonMark
    # has no native table syntax:
    # ```
    # Column A  |  Column B
    # value1    |  value2
    # ```

if __name__ == "__main__":
    flavor_commonmark()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}
