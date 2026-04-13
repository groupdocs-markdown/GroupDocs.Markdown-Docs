---
id: convert-for-rag
url: markdown/net/convert-for-rag
title: Convert documents for RAG pipelines
weight: 1
description: "Prepare PDF, Word, and Excel documents as Markdown for retrieval-augmented generation with LLMs"
keywords: RAG, AI, LLM, retrieval-augmented generation, chunking, embedding
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

Retrieval-augmented generation (RAG) systems need documents in a clean, structured text format for chunking and embedding. Markdown is ideal — it preserves document structure (headings, lists, tables) while being easy to parse.

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

{{< tabs "rag-basic">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Convert document to Markdown — skip images for text-only RAG
var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy(),
    Flavor = MarkdownFlavor.CommonMark
};

string markdown = MarkdownConverter.ToMarkdown("professional-services.pdf", options);

// Split into chunks by headings
string[] chunks = markdown.Split(
    new[] { "\n## ", "\n# " },
    StringSplitOptions.RemoveEmptyEntries);

foreach (string chunk in chunks)
{
    // Send each chunk to your embedding model
    Console.WriteLine($"Chunk ({chunk.Length} chars): {chunk.Substring(0, Math.Min(80, chunk.Length))}...");
}
```
{{< /tab >}}
{{< tab "professional-services.pdf" >}}  
{{< tab-text >}}
`professional-services.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/use-cases/professional-services.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "rag-basic.txt" >}}  
```text
Chunk (7889 chars): 

**Professional Services**

A catalog of engagements offered by Meridian Ou...
```
[Download full output](/markdown/net/_output_files/developer-guide/use-cases/convert-for-rag/RagBasic/rag-basic.txt)
{{< /tab >}}
{{< /tabs >}}

### Batch processing a document library

{{< tabs "rag-batch">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

string[] files = Directory.GetFiles("documents", "*.pdf");

foreach (string file in files)
{
    try
    {
        string markdown = MarkdownConverter.ToMarkdown(file, options);
        string outputPath = Path.ChangeExtension(file, ".md");
        File.WriteAllText(outputPath, markdown);
        Console.WriteLine($"Converted: {file}");
    }
    catch (GroupDocsMarkdownException ex)
    {
        Console.WriteLine($"Skipped {file}: {ex.Message}");
    }
}
```
{{< /tab >}}
{{< tab "rag-batch.zip" >}}  
```text
documents/business-plan.md (7 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/use-cases/convert-for-rag/RagBatch/rag-batch.zip)
{{< /tab >}}
{{< /tabs >}}
