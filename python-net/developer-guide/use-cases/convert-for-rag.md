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

    # Step 2: Convert the document using keyword argument for options
    markdown = MarkdownConverter.to_markdown("business-plan.pdf", convert_options=options)

    # Step 3: Split the Markdown into chunks by heading markers
    chunks = re.split(r"\n#{1,2} ", markdown)

    # Step 4: Process each chunk (e.g., send to an embedding model)
    for chunk in chunks:
        if chunk.strip():
            print(f"Chunk ({len(chunk)} chars): {chunk[:80]}...")

if __name__ == "__main__":
    convert_for_rag()
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/use-cases/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "convert-rag.txt" >}}  
```text
Chunk (36184 chars): 



**HOME**** ****BASED**** ****PROFESSIONAL**** **



**SERVICES**** **



***...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/convert_for_rag/convert-rag.txt)
{{< /tab >}}
{{< tab "convert-rag.txt" >}}  
```text
Chunk (34602 chars): 

**HOME BASED PROFESSIONAL SERVICES *Business Plan* TABLE OF CONTENTS** 

I...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/convert_for_rag/convert-rag.txt)
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

    # Step 3: Convert each file, handling errors gracefully
    for file in files:
        try:
            markdown = MarkdownConverter.to_markdown(file, convert_options=options)
            output_path = os.path.splitext(file)[0] + ".md"
            with open(output_path, "w", encoding="utf-8") as f:
                f.write(markdown)
            print(f"Converted: {file}")
        except GroupDocsMarkdownException as ex:
            print(f"Skipped {file}: {ex}")

if __name__ == "__main__":
    batch_convert_for_rag()
```
{{< /tab >}}
{{< tab "batch-convert-rag.txt" >}}  
```text
Converted: documents\business-plan.pdf
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/batch_convert_for_rag/batch-convert-rag.txt)
{{< /tab >}}
{{< tab "batch-convert-rag.zip" >}}  
```text
documents/business-plan.txt (32 KB)
```
[Download full output](/markdown/python-net/_output_files/developer-guide/use-cases/convert-for-rag/batch_convert_for_rag/batch-convert-rag.zip)
{{< /tab >}}
{{< /tabs >}}
