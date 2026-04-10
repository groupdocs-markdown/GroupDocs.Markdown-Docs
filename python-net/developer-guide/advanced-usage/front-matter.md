---
id: front-matter
url: markdown/python-net/front-matter
title: YAML front matter
weight: 4
description: "Generate YAML front matter from document metadata for static site generators"
keywords: front matter, YAML, Jekyll, Hugo, Docusaurus, metadata
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Enable `include_front_matter` to extract document metadata into a YAML block at the beginning of the Markdown output. This is commonly used by static site generators like Jekyll, Hugo, and Docusaurus.

### Example

{{< tabs "front-matter-example">}}
{{< tab "front_matter_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def front_matter_example():
    """Convert a document to Markdown with YAML front matter extracted from metadata."""

    # Step 1: Enable front matter generation in conversion options
    options = ConvertOptions()
    options.include_front_matter = True

    # Step 2: Convert the document with front matter enabled
    md = MarkdownConverter.to_markdown("business-plan.docx", convert_options=options)

    # Step 3: Print the result -- YAML front matter appears at the top
    print(md)
    # Output:
    # ---
    # title: "Q3 Report"
    # author: "Jane Doe"
    # format: Docx
    # pages: 12
    # ---
    #
    # # Q3 Report
    # ...

if __name__ == "__main__":
    front_matter_example()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter.txt" >}}  
```text
---

format: Docx

pages: 18

---





| HOME BASED |  |  |

| --- | --- | --- |

|  |  |  |

| PROFESSIONAL SERVICES |  |  |

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/front-matter/front_matter_example/front-matter.txt)
{{< /tab >}}
{{< tab "front-matter.txt" >}}  
```text
---
format: Docx
pages: 18
---


| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdI
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/front-matter/front_matter_example/front-matter.txt)
{{< /tab >}}
{{< /tabs >}}

### Combined with heading offset

{{< tabs "front-matter-combined">}}
{{< tab "front_matter_combined.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def front_matter_combined():
    """Convert a document with both YAML front matter and heading level offset."""

    # Step 1: Configure options with front matter and heading offset
    options = ConvertOptions()
    options.include_front_matter = True       # add YAML metadata block
    options.heading_level_offset = 1          # shift headings down one level

    # Step 2: Convert and save to a file using keyword argument for options
    MarkdownConverter.to_file("annual-report.docx", "front-matter-combined.md", convert_options=options)

if __name__ == "__main__":
    front_matter_combined()
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter-combined.txt" >}}  
```text
---
author: "Brianna Thielen"
format: Docx
pages: 1
---

[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]

...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/front-matter/front_matter_combined/front-matter-combined.txt)
{{< /tab >}}
{{< tab "front-matter-combined.txt" >}}  
```text
---
author: "Brianna Thielen"
format: Docx
pages: 1
---

[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]

[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/front-matter/front_matter_combined/front-matter-combined.txt)
{{< /tab >}}
{{< /tabs >}}

### Front matter fields

Only non-empty fields are included:

| Field | Source | Example |
|---|---|---|
| `title` | `BuiltInDocumentProperties.Title` | `"Q3 Report"` |
| `author` | `BuiltInDocumentProperties.Author` | `"Jane Doe"` |
| `format` | Detected file format | `Docx` |
| `pages` | Page or worksheet count | `12` |
