---
id: load-from-a-stream
url: markdown/python-net/load-from-a-stream
title: Load from a stream
weight: 2
description: "This example demonstrates how to load a file from a stream."
keywords: load a file from a stream
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
---

When the source document is not a file on disk (e.g., downloaded from a network, read from a database, or received as an upload), you can pass a binary stream directly to the `MarkdownConverter` constructor.

The stream is copied internally, so you may close it immediately after creating the converter.

{{< tabs "load-stream-basic">}}
{{< tab "load_from_stream.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def load_from_stream():
    """Load a document from a binary stream and convert to Markdown."""

    # Step 1: Open the document file as a binary stream
    with open("business-plan.docx", "rb") as stream:
        # Step 2: Create a converter from the stream
        with MarkdownConverter(stream) as converter:
            # Step 3: Convert and save the Markdown output
            converter.convert("load-from-stream.md")

if __name__ == "__main__":
    load_from_stream()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-from-stream.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream/load-from-stream.txt)
{{< /tab >}}
{{< tab "load-from-stream.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream/load-from-stream.txt)
{{< /tab >}}
{{< /tabs >}}

### Stream with LoadOptions

If the stream does not have a file extension for automatic format detection, specify the format explicitly via `LoadOptions`:

{{< tabs "load-stream-with-options">}}
{{< tab "load_from_stream_with_options.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, LoadOptions, FileFormat

def load_from_stream_with_options():
    """Load a document from a stream with explicit format specification."""

    # Step 1: Open the file as a binary stream
    with open("document", "rb") as stream:
        # Step 2: Specify the file format explicitly (no auto-detection)
        load_options = LoadOptions(FileFormat.DOCX)

        # Step 3: Create a converter from the stream with load options
        with MarkdownConverter(stream, load_options=load_options) as converter:
            # Step 4: Convert and save the Markdown output
            converter.convert("load-from-stream-options.md")

if __name__ == "__main__":
    import shutil
    shutil.copy("business-plan.docx", "document")  # create file without extension
    load_from_stream_with_options()
```
{{< /tab >}}
{{< tab "load-from-stream-options.txt" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream_with_options/load-from-stream-options.txt)
{{< /tab >}}
{{< tab "load-from-stream-options.txt" >}}  
```text
| ![Woman with laptop and business documents](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEA3ADcAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAHyAqYDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIW
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream_with_options/load-from-stream-options.txt)
{{< /tab >}}
{{< /tabs >}}
