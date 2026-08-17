---
id: batch-convert
url: markdown/java/batch-convert
title: Batch-convert a folder
weight: 3
description: "Convert all documents in a directory to Markdown"
keywords: batch, folder, directory, multiple files, bulk
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Convert all supported documents in a directory to Markdown files.

### Basic batch conversion

{{< tabs "batch-basic">}}
{{< tab "BatchBasic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.HashSet;
import java.util.Set;

public class BatchBasic {

    public static void main(String[] args) throws IOException {
        String inputDir = "documents";
        String outputDir = "output";

        Files.createDirectories(Paths.get(outputDir));

        // Get supported extensions
        Set<String> supported = new HashSet<>();
        for (FileFormat format : MarkdownConverter.getSupportedFormats()) {
            supported.add("." + format.toString().toLowerCase());
        }

        int converted = 0;
        int skipped = 0;

        File[] files = new File(inputDir).listFiles();
        if (files == null) {
            files = new File[0];
        }

        for (File file : files) {
            String ext = extension(file.getName());
            if (!supported.contains(ext)) {
                continue;
            }

            String outputPath = new File(outputDir, baseName(file.getName()) + ".md").getPath();

            try {
                MarkdownConverter.toFile(file.getPath(), outputPath);
                converted++;
                System.out.println("OK: " + file.getName());
            } catch (Exception e) {
                skipped++;
                System.out.println("SKIP: " + file.getName() + " — " + e.getMessage());
            }
        }

        System.out.println("Done: " + converted + " converted, " + skipped + " skipped");
    }

    /** Java has no Path.GetExtension / GetFileNameWithoutExtension, so define them once. */
    private static String extension(String fileName) {
        int dot = fileName.lastIndexOf('.');
        return dot < 0 ? "" : fileName.substring(dot).toLowerCase();
    }

    private static String baseName(String fileName) {
        int dot = fileName.lastIndexOf('.');
        return dot < 0 ? fileName : fileName.substring(0, dot);
    }
}
```
{{< /tab >}}
{{< tab "batch-basic.zip" >}}  
```text
output/business-plan.md (278 KB)
output/cost-analysis.md (9 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/batch-convert/BatchBasic/batch-basic.zip)
{{< /tab >}}
{{< /tabs >}}

### Async batch conversion

{{< tabs "batch-async">}}
{{< tab "BatchAsync.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.stream.Collectors;

public class BatchAsync {

    private static final List<String> EXTENSIONS =
            Arrays.asList(".docx", ".pdf", ".xlsx", ".epub");

    public static void main(String[] args) throws IOException {
        String inputDir = "documents";
        String outputDir = "output";

        Files.createDirectories(Paths.get(outputDir));

        File[] files = new File(inputDir).listFiles(
                (dir, name) -> EXTENSIONS.contains(extension(name)));
        if (files == null) {
            files = new File[0];
        }

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new SkipImagesStrategy());

        // toFileAsync already runs off the calling thread — do not wrap in a parallel stream
        List<CompletableFuture<Void>> futures = Arrays.stream(files)
                .map(file -> {
                    String outputPath =
                            new File(outputDir, baseName(file.getName()) + ".md").getPath();

                    return MarkdownConverterAsync.toFileAsync(file.getPath(), outputPath, options)
                            .thenRun(() -> System.out.println("OK: " + file.getName()))
                            .exceptionally(e -> {
                                System.out.println("SKIP: " + file.getName() + " — " + e.getMessage());
                                return null;
                            });
                })
                .collect(Collectors.toList());

        CompletableFuture.allOf(futures.toArray(new CompletableFuture<?>[0])).join();
    }

    private static String extension(String fileName) {
        int dot = fileName.lastIndexOf('.');
        return dot < 0 ? "" : fileName.substring(dot).toLowerCase();
    }

    private static String baseName(String fileName) {
        int dot = fileName.lastIndexOf('.');
        return dot < 0 ? fileName : fileName.substring(0, dot);
    }
}
```
{{< /tab >}}
{{< tab "batch-async.zip" >}}  
```text
output/business-plan.md (7 KB)
output/cost-analysis.md (9 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/batch-convert/BatchAsync/batch-async.zip)
{{< /tab >}}
{{< /tabs >}}
