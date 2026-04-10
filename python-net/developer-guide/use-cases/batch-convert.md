---
id: batch-convert
url: markdown/python-net/batch-convert
title: Batch-convert a folder
weight: 3
description: "Convert all documents in a directory to Markdown"
keywords: batch, folder, directory, multiple files, bulk
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Convert all supported documents in a directory to Markdown files.

### Basic batch conversion

{{< tabs "batch-convert-basic">}}
{{< tab "batch_convert.py" >}}  
```python
import os
from groupdocs.markdown import MarkdownConverter

def batch_convert():
    """Convert all supported documents in a folder to Markdown."""

    # Step 1: Define input and output directories
    input_dir = "documents"
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    converted = 0
    skipped = 0

    # Step 2: Iterate over all files in the input folder
    for filename in os.listdir(input_dir):
        file_path = os.path.join(input_dir, filename)

        # Skip directories
        if not os.path.isfile(file_path):
            continue

        # Build output path with .md extension
        output_path = os.path.join(
            output_dir,
            os.path.splitext(filename)[0] + ".md")

        try:
            # Step 3: Convert each document to Markdown
            MarkdownConverter.to_file(file_path, output_path)
            converted += 1
            print(f"  OK: {filename}")
        except Exception as ex:
            skipped += 1
            print(f"  SKIP: {filename} - {ex}")

    # Step 4: Print summary
    print(f"Done: {converted} converted, {skipped} skipped")

if __name__ == "__main__":
    batch_convert()
```
{{< /tab >}}
{{< tab "batch-convert.zip" >}}  
```text
output/business-plan.txt (288 KB)
output/cost-analysis.txt (1011 bytes)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/batch-convert/batch_convert/batch-convert.zip)
{{< /tab >}}
{{< tab "batch-convert.zip" >}}  
```text
output/business-plan.txt (287 KB)
output/cost-analysis.txt (1011 bytes)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/batch-convert/batch_convert/batch-convert.zip)
{{< /tab >}}
{{< /tabs >}}
