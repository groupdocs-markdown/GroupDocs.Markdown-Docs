---
id: product-overview
url: markdown/python-net/product-overview
title: GroupDocs.Markdown for Python via .NET overview
linkTitle: Product overview
weight: 1
description: "GroupDocs.Markdown for Python via .NET converts documents to clean, structured Markdown with full control over output flavor, image handling, and formatting."
keywords: markdown, PDF, DOCX, XLSX, EPUB, export, LLM, Gen AI, RAG, python
productName: GroupDocs.Markdown for Python via .NET
toc: True
---

## What is GroupDocs.Markdown?

GroupDocs.Markdown for Python via .NET is a Python library that converts documents from 30+ formats (PDF, Word, Excel, EPUB, TXT, CHM) into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

Designed for AI/ML workflows, static site generators, and document processing pipelines — Markdown is the ideal format for language models, text analysis tools, and content management systems.

## Key capabilities

| Capability | Description |
|---|---|
| **30+ input formats** | PDF, DOCX, DOC, XLSX, XLS, CSV, EPUB, MOBI, TXT, CHM, RTF, ODT, and more |
| **Markdown flavors** | [GitHub Flavored Markdown or CommonMark]({{< ref "markdown/python-net/developer-guide/advanced-usage/markdown-flavor" >}}) |
| **Image handling** | [Base64 embed, file system, skip, or custom]({{< ref "markdown/python-net/developer-guide/advanced-usage/strategy/" >}}) with relative paths and image replacement |
| **YAML front matter** | [Auto-extract metadata]({{< ref "markdown/python-net/developer-guide/advanced-usage/front-matter" >}}) for Jekyll, Hugo, Docusaurus |
| **Document inspection** | [Read format, pages, title, author]({{< ref "markdown/python-net/developer-guide/basic-usage/get-document-info" >}}) without converting |
| **Spreadsheet control** | [Column/row truncation]({{< ref "markdown/python-net/developer-guide/advanced-usage/spreadsheet-options" >}}), sheet separators, hidden sheet filtering |
| **Heading offset** | [Shift heading levels]({{< ref "markdown/python-net/developer-guide/advanced-usage/heading-offset" >}}) for content embedding |
| **Async API** | [Non-blocking conversion]({{< ref "markdown/python-net/developer-guide/advanced-usage/async-api" >}}) for web and serverless |
| **Error handling** | [Specific exception types]({{< ref "markdown/python-net/developer-guide/advanced-usage/error-handling" >}}) and conversion warnings |

## Quick example

{{< tabs "quick-example" >}}
{{< tab "quick_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, MarkdownFlavor

def quick_example():
    """Convert a Word document to Markdown with GitHub flavor and YAML front matter."""

    # One-liner
    md = MarkdownConverter.to_markdown("business-plan.docx")
    # # Quarterly Report
    #
    # ## Executive Summary
    #
    # This report covers the key initiatives...

    # With options
    options = ConvertOptions()
    options.flavor = MarkdownFlavor.GIT_HUB
    options.include_front_matter = True
    options.heading_level_offset = 1
    MarkdownConverter.to_file("business-plan.docx", "quick-example.md", convert_options=options)

if __name__ == "__main__":
    quick_example()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "quick-example.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Business Plan"
author: "Meridian Outdoor Co."
format: Docx
pages: 5
---

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/product-overview/quick_example/quick-example.md)
{{< /tab >}}
{{< /tabs >}}

## Platform support

- Windows, Linux, macOS
- Python 3.5 or later
- 64-bit interpreter

## Get started

- [Quick start guide]({{< ref "markdown/python-net/getting-started/quick-start-guide" >}})
- [Installation]({{< ref "markdown/python-net/getting-started/installation" >}})
- [Features overview]({{< ref "markdown/python-net/getting-started/features-overview" >}})
- [API Reference](https://reference.groupdocs.com/markdown/python-net)
