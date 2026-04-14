---
id: convert-for-rag
url: markdown/python-net/convert-for-rag
title: Convert documents for RAG pipelines
weight: 1
description: "Prepare PDF, Word, and Excel documents as Markdown for retrieval-augmented generation with LLMs"
keywords: RAG, AI, LLM, retrieval-augmented generation, chunking, embedding
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

Retrieval-augmented generation (RAG) systems need documents in a clean, structured text format for chunking and embedding. Markdown is ideal -- it preserves document structure (headings, lists, tables) while being easy to parse.

{{< mermaid class="text-center" >}}
flowchart LR
    A["PDF / DOCX / XLSX"]
    B["GroupDocs.Markdown"]
    C["Markdown"]
    D["Text Chunking"]
    E["Vector Embeddings"]
    F["LLM Query"]
    A --> B --> C --> D --> E --> F
{{< /mermaid >}}

### Basic conversion for RAG

{{< tabs "convert-for-rag-basic">}}
{{< tab "convert_for_rag.py" >}}  
```python
import re
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy, MarkdownFlavor

def convert_for_rag():
    """Convert a PDF to Markdown for RAG pipelines, then split into chunks by heading."""

    # Step 1: Configure conversion for text-only RAG (skip images)
    options = ConvertOptions()
    options.image_export_strategy = SkipImagesStrategy()
    options.flavor = MarkdownFlavor.COMMON_MARK

    # Step 2: Convert the document and save it to a Markdown file
    MarkdownConverter.to_file("business-plan.pdf", "convert-for-rag-basic.md", convert_options=options)

    # Step 3: Read the result back and split it into chunks by heading markers
    with open("convert-for-rag-basic.md", "r", encoding="utf-8") as f:
        markdown = f.read()
    chunks = [c for c in re.split(r"\n#{1,2} ", markdown) if c.strip()]

    # Step 4: Write a chunk summary to a text file (ready to feed an embedding model)
    with open("convert-for-rag-basic.txt", "w", encoding="utf-8") as f:
        for i, chunk in enumerate(chunks, 1):
            f.write(f"Chunk {i} ({len(chunk)} chars): {chunk[:80]}...\n")

if __name__ == "__main__":
    convert_for_rag()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/use-cases/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-for-rag-basic.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

**Table of Contents**

Meridian Outdoor Co. — Business Plan .........................................................................................1FY2026 Strategic Plan.................................................................................................................1Table of Contents.............................................................................................................................2

1. Ex
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/convert_for_rag/convert-for-rag-basic.md)
{{< /tab >}}
{{< /tabs >}}

### Batch processing a document library

{{< tabs "batch-convert-for-rag">}}
{{< tab "batch_convert_for_rag.py" >}}  
```python
import os
import glob
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy, GroupDocsMarkdownException

def batch_convert_for_rag():
    """Batch-convert all PDFs in a folder to Markdown for RAG ingestion."""

    # Step 1: Configure conversion to skip images (text-only RAG)
    options = ConvertOptions()
    options.image_export_strategy = SkipImagesStrategy()

    # Step 2: Find all PDF files in the documents folder
    files = glob.glob("documents/*.pdf")

    # Step 3: Convert each file, handling errors gracefully, and write a log
    with open("batch-convert-for-rag.txt", "w", encoding="utf-8") as log:
        for file in files:
            output_path = os.path.splitext(file)[0] + ".md"
            try:
                MarkdownConverter.to_file(file, output_path, convert_options=options)
                log.write(f"Converted: {file}\n")
            except GroupDocsMarkdownException as ex:
                log.write(f"Skipped {file}: {ex}\n")

if __name__ == "__main__":
    batch_convert_for_rag()
```
{{< /tab >}}
{{< tab "batch-convert-rag.zip" >}}  
```text
batch-convert-for-rag.txt (40 bytes)
documents/business-plan.md (7 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/batch_convert_for_rag/batch-convert-rag.zip)
{{< /tab >}}
{{< /tabs >}}
