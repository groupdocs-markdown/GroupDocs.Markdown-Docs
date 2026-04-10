---
id: static-site-generator
url: markdown/python-net/static-site-generator
title: Generate content for static sites
weight: 2
description: "Convert documents to Markdown with YAML front matter for Jekyll, Hugo, and Docusaurus"
keywords: static site, Jekyll, Hugo, Docusaurus, front matter, YAML
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Static site generators like Jekyll, Hugo, and Docusaurus expect Markdown files with YAML front matter. GroupDocs.Markdown can automatically generate front matter from document metadata.

### Convert with front matter and relative images

{{< tabs "static-site-convert">}}
{{< tab "static_site_convert.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, ExportImagesToFileSystemStrategy

def static_site_convert():
    """Convert a DOCX to Markdown with front matter and relative images for static sites."""

    # Step 1: Configure image export with relative paths
    strategy = ExportImagesToFileSystemStrategy("content/posts/images")
    strategy.images_relative_path = "images"

    # Step 2: Set conversion options for static site generators
    options = ConvertOptions()
    options.include_front_matter = True       # add YAML metadata block
    options.heading_level_offset = 1          # reserve H1 for the page title
    options.image_export_strategy = strategy

    # Step 3: Convert and save using keyword argument for options
    MarkdownConverter.to_file(
        "annual-report.docx", "content/posts/annual-report.md",
        convert_options=options)

    # Output file starts with:
    # ---
    # title: "Annual Report 2025"
    # author: "Finance Team"
    # format: Docx
    # pages: 24
    # ---
    #
    # ## Executive Summary
    # ...

if __name__ == "__main__":
    import os
    os.makedirs("content/posts/images", exist_ok=True)
    static_site_convert()
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/use-cases/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "static-site-convert.zip" >}}  
```text
content/posts/annual-report.txt (941 bytes)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/static-site-generator/static_site_convert/static-site-convert.zip)
{{< /tab >}}
{{< tab "static-site-convert.zip" >}}  
```text
content/posts/annual-report.txt (477 bytes)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/static-site-generator/static_site_convert/static-site-convert.zip)
{{< /tab >}}
{{< /tabs >}}

### Batch-convert a folder for Hugo

{{< tabs "batch-convert-for-hugo">}}
{{< tab "batch_convert_for_hugo.py" >}}  
```python
import os
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy

def batch_convert_for_hugo():
    """Batch-convert all documents in a folder to Markdown with YAML front matter for Hugo/Jekyll."""

    # Step 1: Define source and output directories
    input_dir = "documents"
    output_dir = "content/posts"
    os.makedirs(output_dir, exist_ok=True)

    # Step 2: Configure conversion for static site generators
    options = ConvertOptions()
    options.include_front_matter = True          # add YAML metadata block
    options.heading_level_offset = 1             # reserve H1 for Hugo page title
    options.image_export_strategy = SkipImagesStrategy()  # text-only content

    # Step 3: Iterate over all files in the source folder
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
            # Step 4: Convert each file with front matter and heading offset
            MarkdownConverter.to_file(file_path, output_path, convert_options=options)
            print(f"  OK: {filename} -> {output_path}")
        except Exception as ex:
            print(f"  SKIP: {filename} - {ex}")

if __name__ == "__main__":
    batch_convert_for_hugo()
```
{{< /tab >}}
{{< tab "batch-convert-hugo.zip" >}}  
```text
content/posts/business-plan.txt (33 KB)
content/posts/cost-analysis.txt (1 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/static-site-generator/batch_convert_for_hugo/batch-convert-hugo.zip)
{{< /tab >}}
{{< tab "batch-convert-hugo.zip" >}}  
```text
content/posts/business-plan.txt (32 KB)
content/posts/cost-analysis.txt (1 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/static-site-generator/batch_convert_for_hugo/batch-convert-hugo.zip)
{{< /tab >}}
{{< /tabs >}}
