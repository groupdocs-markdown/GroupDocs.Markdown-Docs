---
id: custom-strategy
url: markdown/python-net/custom-strategy
title: Save image by custom strategy
weight: 4
description: "The listed articles below explain how to control how images are saved when a document is saved to Markdown format."
keywords:
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

Use `CustomImagesStrategy` with a Python callable for full control over how each image is saved during conversion. You can rename files, redirect output to a custom stream, or replace image content entirely.

### Rename images with a callable handler

Pass a Python callable to customize saving logic for each image:

{{< tabs "custom-strategy-rename">}}
{{< tab "custom_strategy_rename.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, CustomImagesStrategy

def custom_strategy_rename():
    """Rename images sequentially using a custom image saving handler."""

    # Step 1: Set up an image counter for sequential naming
    counter = [0]

    # Step 2: Define a handler that renames each image
    def rename_handler(call_info):
        """Called for each image during conversion.
        Receives context with ImageFileName, ShapeType, OutputDirectory.
        Returns dict with output actions."""
        ctx = call_info["context"]
        counter[0] += 1
        new_name = f"fig-{counter[0]}.png"
        print(f"  Renaming: {ctx['ImageFileName']} -> {new_name}")
        return {"output_image_file_name": new_name}

    # Step 3: Configure the custom image strategy with the handler
    options = ConvertOptions()
    options.image_export_strategy = CustomImagesStrategy("./output/images", rename_handler)

    # Step 4: Convert -- each image triggers the rename_handler callback
    MarkdownConverter.to_file("business-plan.docx", "output/document.md", convert_options=options)

if __name__ == "__main__":
    import os
    os.makedirs("output/images", exist_ok=True)
    custom_strategy_rename()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-rename.zip" >}}  
```text
output/document.txt (21 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/custom_strategy_rename/custom-strategy-rename.zip)
{{< /tab >}}
{{< tab "custom-strategy-rename.zip" >}}  
```text
output/document.txt (20 KB)
output/images/fig-1.png (56 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/custom_strategy_rename/custom-strategy-rename.zip)
{{< /tab >}}
{{< /tabs >}}

### Replace image content with a placeholder

Use the `replacement_image_path` return value to substitute the original image with different content (e.g., a watermarked version or a placeholder):

{{< tabs "custom-strategy-replace">}}
{{< tab "custom_strategy_replace.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, CustomImagesStrategy

def custom_strategy_replace():
    """Replace every image with a placeholder during conversion."""

    # Step 1: Define a handler that substitutes each image with a placeholder
    def watermark_handler(call_info):
        """Replace every image with a placeholder file."""
        return {
            "output_image_file_name": "placeholder.png",
            "replacement_image_path": "./assets/placeholder.png"
        }

    # Step 2: Configure the custom image strategy with the replacement handler
    options = ConvertOptions()
    options.image_export_strategy = CustomImagesStrategy("./output/images", watermark_handler)

    # Step 3: Convert and save using keyword argument for options
    MarkdownConverter.to_file("business-plan.docx", "output/document.md", convert_options=options)

if __name__ == "__main__":
    import os
    os.makedirs("output/images", exist_ok=True)
    custom_strategy_replace()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-replace.zip" >}}  
```text
output/document.txt (21 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/custom_strategy_replace/custom-strategy-replace.zip)
{{< /tab >}}
{{< tab "custom-strategy-replace.zip" >}}  
```text
output/document.txt (20 KB)
output/images/placeholder.png (56 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/custom_strategy_replace/custom-strategy-replace.zip)
{{< /tab >}}
{{< /tabs >}}

### Callback response keys

Return a dictionary with one or more of the following keys. Return `None` or `{}` to keep defaults. Exceptions raised in handlers are re-raised with the original type and traceback.

| Response key | Effect |
|---|---|
| `output_image_file_name` | Override the image file name |
| `replacement_image_path` | Replace the image with a file at the given path |
| `output_stream_path` | Redirect image data to a file at the given path |

The handler receives a `call_info` dictionary with a `"context"` key containing `ImageFileName`, `ShapeType`, and `OutputDirectory`.
