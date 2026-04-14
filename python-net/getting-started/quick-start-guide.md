---
id: quick-start-guide
url: markdown/python-net/quick-start-guide
title: Quick start guide
weight: 0
description: "Get started with GroupDocs.Markdown for Python via .NET in minutes -- convert documents to Markdown with a single line of code"
keywords: quick start, getting started, convert, example, python
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

This guide shows you how to convert documents to Markdown with GroupDocs.Markdown for Python via .NET. You'll have working code in under 2 minutes.

### How it works

{{< mermaid class="text-center" >}}
flowchart LR
    A["Input Document\n(DOCX, PDF, XLSX, EPUB, ...)"]
    B["MarkdownConverter"]
    C["Markdown Output\n(.md file or string)"]
    A --> B --> C
{{< /mermaid >}}

### Prerequisites

1. Install the package from PyPI:

```bash
pip install groupdocs-markdown-net
```

2. Import the module:

{{< tabs "import-module">}}
{{< tab "import_module.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter
```
{{< /tab >}}
{{< /tabs >}}

### Example 1: Convert Word to Markdown

The simplest conversion -- one line of code:

{{< tabs "quick-start-word">}}
{{< tab "convert_word_to_markdown.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def convert_word_to_markdown():
    """Convert a Word document to Markdown in one line of code."""

    # Convert a DOCX file directly to a Markdown file on disk
    MarkdownConverter.to_file("business-plan.docx", "quick-start-word.md")

if __name__ == "__main__":
    convert_word_to_markdown()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/getting-started/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "quick-start-word.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/getting-started/quick-start-guide/convert_word_to_markdown/quick-start-word.md)
{{< /tab >}}
{{< /tabs >}}

### Example 2: Convert PDF with image export

Save a PDF to Markdown with images extracted to a folder:

{{< tabs "quick-start-pdf">}}
{{< tab "convert_pdf_with_images.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def convert_pdf_with_images():
    """Convert a PDF to Markdown with images exported to a folder on disk."""

    # Step 1: Configure image export with relative paths
    strategy = ExportImagesToFileSystemStrategy("output/images")
    strategy.images_relative_path = "images"

    # Step 2: Assign the strategy to conversion options
    options = ConvertOptions()
    options.image_export_strategy = strategy

    # Step 3: Convert and save using keyword argument for options
    MarkdownConverter.to_file("business-plan.pdf", "output/report.md", convert_options=options)
    # Images saved to output/images/
    # Markdown references: ![](images/img-001.png)

if __name__ == "__main__":
    import os
    os.makedirs("output/images", exist_ok=True)
    convert_pdf_with_images()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/getting-started/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-pdf-with-images.zip" >}}  
```text
output/images/img-001.png (3 KB)
output/images/img-002.jpg (73 KB)
output/images/img-003.jpg (76 KB)
output/report.md (7 KB)
```
[Download full output](/markdown/python-net/_output_files/getting-started/quick-start-guide/convert_pdf_with_images/convert-pdf-with-images.zip)
{{< /tab >}}
{{< /tabs >}}

### Example 3: Convert Excel with options

Convert a spreadsheet with column truncation and front matter:

{{< tabs "quick-start-excel">}}
{{< tab "convert_excel_with_options.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, MarkdownFlavor

def convert_excel_with_options():
    """Convert an Excel spreadsheet with column/row limits, front matter, and GFM flavor."""

    # Step 1: Configure spreadsheet-specific conversion options
    options = ConvertOptions()
    options.max_columns = 8              # limit to first 8 columns
    options.max_rows = 50                # limit to first 50 data rows
    options.include_front_matter = True  # add YAML metadata block
    options.flavor = MarkdownFlavor.GIT_HUB  # GitHub Flavored Markdown

    # Step 2: Open the spreadsheet with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 3: Convert and save the Markdown output
        converter.convert("quick-start-excel.md", convert_options=options)

if __name__ == "__main__":
    convert_excel_with_options()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/getting-started/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "quick-start-excel.md" >}}  
```text
---
format: Xlsx
pages: 4
---


## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/getting-started/quick-start-guide/convert_excel_with_options/quick-start-excel.md)
{{< /tab >}}
{{< /tabs >}}

### What's next?

- [Supported document formats]({{< ref "markdown/python-net/getting-started/supported-document-formats.md" >}}) -- full list of input formats
- [Image handling strategies]({{< ref "markdown/python-net/developer-guide/advanced-usage/strategy" >}}) -- Base64, file system, skip, custom
- [Markdown flavor control]({{< ref "markdown/python-net/developer-guide/advanced-usage/markdown-flavor.md" >}}) -- GitHub vs CommonMark
- [YAML front matter]({{< ref "markdown/python-net/developer-guide/advanced-usage/front-matter.md" >}}) -- for static site generators
