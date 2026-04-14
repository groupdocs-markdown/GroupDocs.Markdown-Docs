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
{{< tab "load-password-static.md" >}}  
```text
**Confidential Memo**

From: Meridian Outdoor Co. — Strategy Team

Date: 2026-01-15

Subject: FY2026 M&A Targets



[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_static/load-password-static.md)
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
{{< tab "load-password-instance.md" >}}  
```text
## Expenses

| Date | Vendor | Category | Amount |
| --- | --- | --- | --- |
| 2026-01-02 | Pacific Freight | Shipping | $2,450.00 |
| 2026-01-05 | Cedar Packaging | Materials | $1,320.50 |
| 2026-01-08 | Highline Textiles | Materials | $8,940.00 |
| 2026-01-12 | Portland Electric | Utilities | $680.25 |
| 2026-01-14 | Backcountry Co-op | Events | $1,200.00 |
| 2026-01-17 | Ridge Media | Marketing | $5,400.00 |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_instance/load-password-instance.md)
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
        MarkdownConverter.to_file("protected.docx", "load-password-exception.md")
    except DocumentProtectedException as ex:
        # Step 2: Catch the exception and write a user-friendly message to a file
        with open("load-password-exception.txt", "w", encoding="utf-8") as f:
            f.write(f"Cannot open document: {ex}\n")

if __name__ == "__main__":
    load_password_exception()
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-exception.md" >}}  
{{< tab-text >}}
`load-password-exception.md` is the output produced by this example. Click [here](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/load_password_exception/load-password-exception.md) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}
