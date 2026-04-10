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

md = MarkdownConverter.to_markdown("business-plan.docx")
MarkdownConverter.to_file("business-plan.docx", "convert-static.md")
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Instance API

Create a [MarkdownConverter](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown/markdownconverter/) instance for advanced scenarios such as inspecting metadata before converting or reusing a loaded document:

{{< tabs "convert-instance-api">}}
{{< tab "convert_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

with MarkdownConverter("business-plan.docx") as converter:
    options = ConvertOptions()
    options.heading_level_offset = 1

    converter.convert("convert-instance.md", convert_options=options)
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Conversion options

Use [ConvertOptions](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown/convertoptions/) to customize the output -- select specific pages, control image handling, choose a Markdown flavor, add YAML front matter, and more. For loading customization, use [LoadOptions](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown.options.load) to specify file format or provide a password.

These documentation articles explain how to convert files from the most popular formats:
