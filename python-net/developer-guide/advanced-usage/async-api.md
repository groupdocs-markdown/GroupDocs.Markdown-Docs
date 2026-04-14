---
id: async-api
url: markdown/python-net/async-api
title: Async API
weight: 8
description: "Use async methods for non-blocking document conversion in web apps and serverless"
keywords: async, await, asynchronous, asyncio, web, serverless, python
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

All static and instance methods have async counterparts. File I/O is truly asynchronous — source files are read and output files are written using async streams, while the CPU-bound conversion itself runs on a worker thread so your event loop stays responsive.

{{< alert style="info" >}}
Async methods are designed for use with Python's built-in `asyncio` framework. Call them with `await` from inside a coroutine and run the coroutine with `asyncio.run()`.
{{< /alert >}}

### Static async methods

{{< tabs "async-static">}}
{{< tab "async_static.py" >}}  
```python
import asyncio
from groupdocs.markdown import MarkdownConverter, ConvertOptions

async def async_static():
    """Use the static async API to convert a document and inspect its metadata."""

    # Step 1: Convert to a Markdown string
    md = await MarkdownConverter.to_markdown_async("business-plan.docx")

    # Step 2: Convert and save directly to a file
    await MarkdownConverter.to_file_async("business-plan.docx", "async-static.md", None)

    # Step 3: Convert with options
    options = ConvertOptions()
    options.include_front_matter = True
    await MarkdownConverter.to_file_async("business-plan.docx", "async-static.md", options)

    # Step 4: Retrieve document info without a full conversion
    info = await MarkdownConverter.get_info_async("business-plan.docx", None)
    # info.file_format, info.page_count

if __name__ == "__main__":
    asyncio.run(async_static())
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-static.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Business Plan"
author: "Meridian Outdoor Co."
format: Docx
pages: 5
---

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/async-api/async_static/async-static.md)
{{< /tab >}}
{{< /tabs >}}

### Instance async methods

{{< tabs "async-instance">}}
{{< tab "async_instance.py" >}}  
```python
import asyncio
from groupdocs.markdown import MarkdownConverter, ConvertOptions

async def async_instance():
    """Use the instance async API with a context manager."""

    # Step 1: Open the document with a context manager
    with MarkdownConverter("business-plan.docx") as converter:
        # Step 2: Configure conversion options
        options = ConvertOptions()
        options.heading_level_offset = 1

        # Step 3: Convert and save the Markdown output asynchronously
        await converter.convert_async("async-instance.md", options)

        # Step 4: Retrieve document metadata asynchronously
        info = await converter.get_document_info_async()
        # info.file_format, info.page_count

if __name__ == "__main__":
    asyncio.run(async_instance())
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-instance.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/async-api/async_instance/async-instance.md)
{{< /tab >}}
{{< /tabs >}}

### Running concurrent conversions

Use `asyncio.gather()` to convert multiple documents in parallel while the event loop stays free for other work:

{{< tabs "async-concurrent">}}
{{< tab "async_concurrent.py" >}}  
```python
import asyncio
from groupdocs.markdown import MarkdownConverter

async def async_concurrent():
    """Convert several documents concurrently with asyncio.gather()."""

    # Step 1: Define the source files and their output targets
    jobs = [
        ("business-plan.docx", "async-concurrent-docx.md"),
        ("business-plan.pdf",  "async-concurrent-pdf.md"),
        ("cost-analysis.xlsx", "async-concurrent-xlsx.md"),
    ]

    # Step 2: Launch every conversion concurrently
    await asyncio.gather(*(
        MarkdownConverter.to_file_async(src, dst, None) for src, dst in jobs
    ))

if __name__ == "__main__":
    asyncio.run(async_concurrent())
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-concurrent-docx.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/async-api/async_concurrent/async-concurrent-docx.md)
{{< /tab >}}
{{< /tabs >}}

### FastAPI example

The async API is a natural fit for ASGI frameworks such as FastAPI — file I/O does not block the event loop, so a single worker can handle many concurrent conversion requests:

{{< tabs "async-fastapi">}}
{{< tab "async_fastapi.py" >}}  
```python
import os
import tempfile
from fastapi import FastAPI, UploadFile
from fastapi.responses import PlainTextResponse
from groupdocs.markdown import MarkdownConverter, ConvertOptions, MarkdownFlavor

app = FastAPI()

@app.post("/convert", response_class=PlainTextResponse)
async def async_fastapi(file: UploadFile):
    """Accept an uploaded document and return Markdown without blocking the event loop."""
    # Stream the upload to a temp file so GroupDocs.Markdown can open it
    suffix = os.path.splitext(file.filename)[1]
    with tempfile.NamedTemporaryFile(delete=False, suffix=suffix) as tmp:
        tmp.write(await file.read())
        tmp_path = tmp.name

    options = ConvertOptions()
    options.flavor = MarkdownFlavor.GIT_HUB

    try:
        return await MarkdownConverter.to_markdown_async(tmp_path, convert_options=options)
    finally:
        os.unlink(tmp_path)
```
{{< /tab >}}
{{< /tabs >}}
