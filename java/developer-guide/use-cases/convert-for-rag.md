---
id: convert-for-rag
url: markdown/java/convert-for-rag
title: Convert documents for RAG pipelines
weight: 1
description: "Prepare PDF, Word, and Excel documents as Markdown for retrieval-augmented generation with LLMs"
keywords: RAG, AI, LLM, retrieval-augmented generation, chunking, embedding
productName: GroupDocs.Markdown for Java
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
{{< tab "RagBasic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.util.regex.Pattern;

public class RagBasic {

    // Matches a newline followed by a level-1 or level-2 heading marker
    private static final Pattern HEADING = Pattern.compile("\\n#{1,2} ");

    public static void main(String[] args) {
        // Convert document to Markdown — skip images for text-only RAG
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new SkipImagesStrategy());
        options.setFlavor(MarkdownFlavor.COMMON_MARK);

        String markdown = MarkdownConverter.toMarkdown("professional-services.pdf", options);

        // Split into chunks by headings
        String[] chunks = HEADING.split(markdown);

        for (String chunk : chunks) {
            if (chunk.isEmpty()) {
                continue;
            }
            // Send each chunk to your embedding model
            String preview = chunk.substring(0, Math.min(80, chunk.length()));
            System.out.println("Chunk (" + chunk.length() + " chars): " + preview + "...");
        }
    }
}
```
{{< /tab >}}
{{< tab "professional-services.pdf" >}}  
{{< tab-text >}}
`professional-services.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/use-cases/professional-services.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "rag-basic.txt" >}}  
```text
Chunk (8065 chars): 
**Professional Services**

A catalog of engagements offered by Meridian Outd...
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/convert-for-rag/RagBasic/rag-basic.txt)
{{< /tab >}}
{{< /tabs >}}

### Batch processing a document library

{{< tabs "rag-batch">}}
{{< tab "RagBatch.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Paths;

public class RagBatch {

    public static void main(String[] args) throws IOException {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new SkipImagesStrategy());

        File[] files = new File("documents").listFiles(
                (dir, name) -> name.toLowerCase().endsWith(".pdf"));
        if (files == null) {
            files = new File[0];
        }

        for (File file : files) {
            try {
                String markdown = MarkdownConverter.toMarkdown(file.getPath(), options);
                String outputPath = changeExtension(file.getPath(), ".md");
                Files.write(Paths.get(outputPath), markdown.getBytes(StandardCharsets.UTF_8));
                System.out.println("Converted: " + file.getPath());
            } catch (GroupDocsMarkdownException e) {
                System.out.println("Skipped " + file.getPath() + ": " + e.getMessage());
            }
        }
    }

    /** Java has no Path.ChangeExtension equivalent. */
    private static String changeExtension(String path, String newExtension) {
        int dot = path.lastIndexOf('.');
        return (dot < 0 ? path : path.substring(0, dot)) + newExtension;
    }
}
```
{{< /tab >}}
{{< tab "rag-batch.txt" >}}  
```text
Converted: documents\business-plan.pdf
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/convert-for-rag/RagBatch/rag-batch.txt)
{{< /tab >}}
{{< /tabs >}}
