---
id: static-site-generator
url: markdown/java/static-site-generator
title: Generate content for static sites
weight: 2
description: "Convert documents to Markdown with YAML front matter for Jekyll, Hugo, and Docusaurus"
keywords: static site, Jekyll, Hugo, Docusaurus, front matter, YAML
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Static site generators like Jekyll, Hugo, and Docusaurus expect Markdown files with YAML front matter. GroupDocs.Markdown can automatically generate front matter from document metadata.

### Convert with front matter and relative images

{{< tabs "ssg-example">}}
{{< tab "SsgExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class SsgExample {

    public static void main(String[] args) {
        ExportImagesToFileSystemStrategy imageStrategy =
                new ExportImagesToFileSystemStrategy("content/posts/images");
        imageStrategy.setImagesRelativePath("images");

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setIncludeFrontMatter(true);
        options.setHeadingLevelOffset(1);   // Reserve H1 for the page title
        options.setImageExportStrategy(imageStrategy);

        MarkdownConverter.toFile("annual-report.docx", "content/posts/annual-report.md", options);

        // Output file starts with:
        // ---
        // title: "Annual Report 2025"
        // author: "Finance Team"
        // format: Docx
        // pages: 24
        // ---
        //
        // ## Executive Summary
        // ...
    }
}
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/use-cases/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "ssg.zip" >}}  
```text
content/posts/annual-report.md (5 KB)
content/posts/images/img-001.png (4 KB)
content/posts/images/img-002.png (14 KB)
content/posts/images/img-003.png (15 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/static-site-generator/SsgExample/ssg.zip)
{{< /tab >}}
{{< /tabs >}}

### Batch-convert a folder for Hugo

{{< tabs "ssg-batch-hugo">}}
{{< tab "SsgBatchHugo.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;
import java.util.Arrays;
import java.util.List;

public class SsgBatchHugo {

    private static final List<String> EXTENSIONS =
            Arrays.asList(".docx", ".pdf", ".xlsx", ".epub");

    public static void main(String[] args) {
        String inputDir = "documents";
        String outputDir = "content/docs";

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setIncludeFrontMatter(true);
        options.setHeadingLevelOffset(1);
        options.setImageExportStrategy(new SkipImagesStrategy());   // or file system

        File[] files = new File(inputDir).listFiles();
        if (files == null) {
            files = new File[0];
        }

        for (File file : files) {
            if (!EXTENSIONS.contains(extension(file.getName()))) {
                continue;
            }

            try {
                String outputPath =
                        new File(outputDir, baseName(file.getName()) + ".md").getPath();

                MarkdownConverter.toFile(file.getPath(), outputPath, options);
                System.out.println("Converted: " + file.getName());
            } catch (Exception e) {
                System.out.println("Skipped: " + file.getName() + " — " + e.getMessage());
            }
        }
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
{{< tab "ssg-batch-hugo.zip" >}}  
```text
content/docs/business-plan.md (0 bytes)
content/docs/cost-analysis.md (9 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/use-cases/static-site-generator/SsgBatchHugo/ssg-batch-hugo.zip)
{{< /tab >}}
{{< /tabs >}}
