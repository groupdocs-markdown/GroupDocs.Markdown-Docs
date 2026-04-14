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

    # Step 2: Convert the document and save it to a Markdown file
    MarkdownConverter.to_file("annual-report.docx", "heading-offset-example.md", convert_options=options)

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
{{< tab "heading-offset-example.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/heading-offset/heading_offset_example/heading-offset-example.md)
{{< /tab >}}
{{< /tabs >}}
