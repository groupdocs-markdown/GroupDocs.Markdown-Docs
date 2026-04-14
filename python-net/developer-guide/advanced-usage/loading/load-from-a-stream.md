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
            converter.convert("load-stream-basic.md")

if __name__ == "__main__":
    load_from_stream()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-stream-basic.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream/load-stream-basic.md)
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
            converter.convert("load-stream-with-options.md")

if __name__ == "__main__":
    import shutil
    shutil.copy("business-plan.docx", "document")  # create file without extension
    load_from_stream_with_options()
```
{{< /tab >}}
{{< tab "load-stream-with-options.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/load_from_stream_with_options/load-stream-with-options.md)
{{< /tab >}}
{{< /tabs >}}
