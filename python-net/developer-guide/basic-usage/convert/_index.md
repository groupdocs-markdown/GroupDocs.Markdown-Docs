---
id: convert
url: markdown/python-net/convert
title: Convert files to various formats
weight: 1
description: "Articles listed in this page explain the common usage scenarios when documents are stored in a local drive and you want to manage them using GroupDocs.Markdown API"
keywords: common usage
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
structuredData:
    showOrganization: True
---

**[GroupDocs.Markdown](https://products.groupdocs.com/markdown/python-net)** provides a quick and easy way to convert documents into clean, structured Markdown. The library offers two approaches: **static methods** for one-line conversions and an **instance API** for more control.

### Static methods (simplest)

Call `MarkdownConverter.to_markdown()` to get a Markdown string, or `MarkdownConverter.to_file()` to write directly to disk:

{{< tabs "convert-static-methods">}}
{{< tab "convert_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def convert_static():
    """Convert a document to Markdown using the static one-liner API."""
    MarkdownConverter.to_file("business-plan.docx", "convert-static-methods.md")

if __name__ == "__main__":
    convert_static()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-static-methods.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/_index/convert_static/convert-static-methods.md)
{{< /tab >}}
{{< /tabs >}}

### Instance API

Create a [MarkdownConverter](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown/markdownconverter/) instance for advanced scenarios such as inspecting metadata before converting or reusing a loaded document:

{{< tabs "convert-instance-api">}}
{{< tab "convert_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def convert_instance():
    """Convert a document using the instance API with conversion options."""
    with MarkdownConverter("business-plan.docx") as converter:
        options = ConvertOptions()
        options.heading_level_offset = 1

        converter.convert("convert-instance-api.md", convert_options=options)

if __name__ == "__main__":
    convert_instance()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-instance-api.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/basic-usage/convert/_index/convert_instance/convert-instance-api.md)
{{< /tab >}}
{{< /tabs >}}

### Conversion options

Use [ConvertOptions](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown/convertoptions/) to customize the output -- select specific pages, control image handling, choose a Markdown flavor, add YAML front matter, and more. For loading customization, use [LoadOptions](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown.options.load) to specify file format or provide a password.

These documentation articles explain how to convert files from the most popular formats:
