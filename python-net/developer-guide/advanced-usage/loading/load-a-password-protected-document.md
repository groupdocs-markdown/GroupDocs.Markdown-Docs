---
id: load-a-password-protected-document
url: markdown/python-net/load-a-password-protected-document
title: Load a password-protected document
weight: 4
description: "This example demonstrates how to load a password-protected document."
keywords: load a password-protected document
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

To open a password-protected document, create a `LoadOptions` instance with the file format and set the `password` property.

{{< tabs "load-password-static">}}
{{< tab "load_password_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, LoadOptions, FileFormat

def load_password_static():
    """Open a password-protected document and convert using the static API."""

    # Step 1: Create load options with format and password
    load_options = LoadOptions(FileFormat.DOCX)
    load_options.password = "secret"

    # Step 2: Convert the protected document using keyword argument
    MarkdownConverter.to_file("protected.docx", "load-password-static.md", load_options=load_options)

if __name__ == "__main__":
    load_password_static()
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-static.txt" >}}  
```text
# **Title of the document**


## **Subtitle #1**

Text is normal, then **bold**, then *italic*, then underscore, and finally normal again. Now ~~strikethrough~~, then double strikethrough, and underscore differently - with dashes. Another underscore is marked with yellow wave line. And then – underscore and strikethrough ~~together~~! Here we have a superscript123 and a subscript456. This part of text has a red background. These words are shadowed to right side, these – shadowed (red) to top sid
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_static/load-password-static.txt)
{{< /tab >}}
{{< tab "load-password-static.txt" >}}  
```text
# **Title of the document**


## **Subtitle #1**

Text is normal, then **bold**, then *italic*, then underscore, and finally normal again. Now ~~strikethrough~~, then double strikethrough, and underscore differently - with dashes. Another underscore is marked with yellow wave line. And then – underscore and strikethrough ~~together~~! Here we have a superscript123 and a subscript456. This part of text has a red background. These words are shadowed to right side, these – shadowed (red) to top sid
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_static/load-password-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "load-password-instance">}}
{{< tab "load_password_instance.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, LoadOptions, FileFormat

def load_password_instance():
    """Open a password-protected spreadsheet and convert using the instance API."""

    # Step 1: Create load options with format and password
    load_options = LoadOptions(FileFormat.XLSX)
    load_options.password = "secret"

    # Step 2: Open the protected document using keyword argument for load options
    with MarkdownConverter("protected.xlsx", load_options=load_options) as converter:
        # Step 3: Convert and save the Markdown output
        converter.convert("load-password-instance.md")

if __name__ == "__main__":
    load_password_instance()
```
{{< /tab >}}
{{< tab "protected.xlsx" >}}  
{{< tab-text >}}
`protected.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/protected.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-instance.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_instance/load-password-instance.txt)
{{< /tab >}}
{{< tab "load-password-instance.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_instance/load-password-instance.txt)
{{< /tab >}}
{{< /tabs >}}

### Handling incorrect passwords

If the password is missing or incorrect, a `DocumentProtectedException` is raised. You can catch it to display a user-friendly message:

{{< tabs "load-password-exception">}}
{{< tab "load_password_exception.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, DocumentProtectedException

def load_password_exception():
    """Handle incorrect or missing passwords when opening protected documents."""

    try:
        # Step 1: Attempt to convert without providing a password
        markdown = MarkdownConverter.to_markdown("protected.docx")
    except DocumentProtectedException as ex:
        # Step 2: Catch the exception and display a user-friendly message
        print(f"Cannot open document: {ex}")

if __name__ == "__main__":
    load_password_exception()
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-exception.txt" >}}  
```text
Cannot open document: The document password is incorrect.
[.NET GroupDocs.Markdown.DocumentProtectedException]
   at .(Stream , LoadOptions )

   at .(Stream , LoadOptions , ConvertOptions , Stream )

   at GroupDocs.Markdown.MarkdownConverter.(ConvertOptions , Stream , Boolean )

   at GroupDocs.Markdown.MarkdownConverter.Convert(ConvertOptions convertOptions)

   at GroupDocs.Markdown.MarkdownConverter.ToMarkdown(String sourcePath, LoadOptions loadOptions, ConvertOptions
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_exception/load-password-exception.txt)
{{< /tab >}}
{{< tab "load-password-exception.txt" >}}  
```text
Cannot open document: The document password is incorrect.
[.NET GroupDocs.Markdown.DocumentProtectedException]
   at .(Stream , LoadOptions )
   at .(Stream , LoadOptions , ConvertOptions , Stream )
   at GroupDocs.Markdown.MarkdownConverter.(ConvertOptions , Stream , Boolean )
   at GroupDocs.Markdown.MarkdownConverter.Convert(ConvertOptions convertOptions)
   at GroupDocs.Markdown.MarkdownConverter.ToMarkdown(String sourcePath, LoadOptions loadOptions, ConvertOptions
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_exception/load-password-exception.txt)
{{< /tab >}}
{{< /tabs >}}
