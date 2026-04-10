---
id: as-base64-strategy
url: markdown/python-net/as-base64-strategy
title: Save image as base64
weight: 1
description: "The listed articles below explain how to embed images as Base64 strings directly in the Markdown."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

By default, `ConvertOptions` uses `ExportImagesAsBase64Strategy`, which embeds images as Base64 data URIs directly in the Markdown output. This keeps the output self-contained in a single file with no external image dependencies.

### Using static method

{{< tabs "base64-static">}}
{{< tab "base64_static.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def base64_static():
    """Convert a PDF to Markdown with images embedded as Base64 (default behavior)."""

    # Step 1: Convert the document -- images are embedded as Base64 by default
    markdown = MarkdownConverter.to_markdown("business-plan.pdf")

    # Step 2: Print the self-contained Markdown output
    print(markdown)

if __name__ == "__main__":
    base64_static()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-static.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/base64_static/base64-static.txt)
{{< /tab >}}
{{< tab "base64-static.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/base64_static/base64-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Specifying the strategy explicitly

If you want to be explicit, set `image_export_strategy` to a new `ExportImagesAsBase64Strategy`:

{{< tabs "base64-explicit">}}
{{< tab "base64_explicit.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, ExportImagesAsBase64Strategy

def base64_explicit():
    """Explicitly set the Base64 image strategy and convert using the instance API."""

    # Step 1: Explicitly configure the Base64 image export strategy
    options = ConvertOptions()
    options.image_export_strategy = ExportImagesAsBase64Strategy()

    # Step 2: Open the document with a context manager
    with MarkdownConverter("business-plan.pdf") as converter:
        # Step 3: Convert using keyword argument for options
        converter.convert("base64-explicit.md", convert_options=options)

if __name__ == "__main__":
    base64_explicit()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-explicit.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/base64_explicit/base64-explicit.txt)
{{< /tab >}}
{{< tab "base64-explicit.txt" >}}  
```text
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAHyAqYDASIAAhEBAxEB/8QAHQAAAgMBAQEBAQAAAAAAAAAABQYABAcIAwEJAv/EAGoQAAACBAoGBwMHBQkNBQYFBQEDAAQFERMhMUFRYXGBofAGFJGxweEHFSMkMzTRQ0TxAhYlNVJUghJFVWR0JjZCU2NldYSiCBciMkZWYmaFkpSy4naGlbTCc5akpcXSN7XE1eZyprbG1P/EABwBAAMAAwEBAQAAAAAAAAAAAAAEBQEDBgIHCP/EAD8RAAIAA
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/base64_explicit/base64-explicit.txt)
{{< /tab >}}
{{< /tabs >}}
