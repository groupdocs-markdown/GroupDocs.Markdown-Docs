---
id: async-api
url: markdown/java/async-api
title: Async API
weight: 8
description: "Use async methods for non-blocking document conversion in web apps and serverless"
keywords: async, asynchronous, web, serverless, CompletableFuture
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

The asynchronous API lives on its own class, **`MarkdownConverterAsync`**, and is entirely static — there is no async counterpart on a `MarkdownConverter` instance. Every method returns a `java.util.concurrent.CompletableFuture`, so you can compose conversions, wait with a timeout, or cancel them.

{{< alert style="info" >}}
The async API requires Java 8 or later, which is where `CompletableFuture` was introduced.
{{< /alert >}}

### Available methods

| Method | Returns |
|---|---|
| `toMarkdownAsync(String)` | `CompletableFuture<String>` |
| `toMarkdownAsync(String, LoadOptions, DocumentConvertOptions)` | `CompletableFuture<String>` |
| `toFileAsync(String, String, DocumentConvertOptions)` | `CompletableFuture<Void>` |
| `getInfoAsync(String, LoadOptions)` | `CompletableFuture<DocumentInfo>` |

Note that `toFileAsync` and `getInfoAsync` have no short overloads — pass `null` for options you do not need.

### Converting asynchronously

{{< tabs "async-static">}}
{{< tab "AsyncStatic.java" >}}
```java
import com.groupdocs.markdown.*;

public class AsyncStatic {

    public static void main(String[] args) {
        // Convert to string
        String md = MarkdownConverterAsync.toMarkdownAsync("business-plan.docx").join();

        // Convert to file — options are required, pass null for the defaults
        MarkdownConverterAsync.toFileAsync("business-plan.docx", "report.md", null).join();

        // With options
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setIncludeFrontMatter(true);
        String withFrontMatter =
                MarkdownConverterAsync.toMarkdownAsync("business-plan.docx", null, options).join();

        // Get document info
        DocumentInfo info = MarkdownConverterAsync.getInfoAsync("business-plan.docx", null).join();
        System.out.println(info.getFileFormat() + ", " + info.getPageCount() + " pages");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "report.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/async-api/AsyncStatic/report.md)
{{< /tab >}}
{{< /tabs >}}

### Converting several documents concurrently

Because each call returns a future, several conversions can be in flight at once. `CompletableFuture.allOf` waits for the whole batch:

{{< tabs "async-concurrent">}}
{{< tab "AsyncConcurrent.java" >}}
```java
import com.groupdocs.markdown.*;

import java.util.concurrent.CompletableFuture;

public class AsyncConcurrent {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setHeadingLevelOffset(1);

        CompletableFuture<Void> word =
                MarkdownConverterAsync.toFileAsync("business-plan.docx", "async-word.md", options);
        CompletableFuture<Void> pdf =
                MarkdownConverterAsync.toFileAsync("business-plan.pdf", "async-pdf.md", options);

        // Wait for both to finish
        CompletableFuture.allOf(word, pdf).join();

        System.out.println("Both conversions complete.");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-pdf.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

![](data:...;base64,[elided])


**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/async-api/AsyncConcurrent/async-pdf.md)
{{< /tab >}}
{{< /tabs >}}

### Cancellation and timeouts

Cancellation is carried by the returned `CompletableFuture` rather than by a separate token parameter. Wait with a timeout using `get(long, TimeUnit)`, and cancel the future if it expires:

{{< tabs "async-cancellation">}}
{{< tab "AsyncCancellation.java" >}}
```java
import com.groupdocs.markdown.*;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

public class AsyncCancellation {

    public static void main(String[] args) throws Exception {
        CompletableFuture<Void> future = MarkdownConverterAsync.toFileAsync(
                "professional-services.pdf",
                "async-cancellation.md",
                null);

        try {
            future.get(30, TimeUnit.SECONDS);
        } catch (TimeoutException e) {
            future.cancel(true);   // interrupt the running conversion
            System.out.println("Conversion timed out.");
        }
    }
}
```
{{< /tab >}}
{{< tab "professional-services.pdf" >}}  
{{< tab-text >}}
`professional-services.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/professional-services.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-cancellation.md" >}}  
```text
**Professional Services**

A catalog of engagements offered by Meridian Outdoor Co.

![](data:...;base64,[elided])![](data:...;base64,[elided])


**Overview**

This catalog describes the six professional services that Meridian offers to partners, wholesalers,
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/async-api/AsyncCancellation/async-cancellation.md)
{{< /tab >}}
{{< /tabs >}}

### Spring Boot example

An upload endpoint that converts in a worker thread and returns the Markdown. The instance API is synchronous, so wrap it in `CompletableFuture.supplyAsync` to keep the request thread free:

{{< tabs "async-spring">}}
{{< tab "AsyncSpring.java" >}}
```java
import com.groupdocs.markdown.*;

import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;

import java.io.IOException;
import java.io.InputStream;
import java.util.concurrent.CompletableFuture;

@RestController
@RequestMapping("/api/convert")
public class AsyncSpring {

    @PostMapping("/to-markdown")
    public CompletableFuture<ResponseEntity<String>> convertToMarkdown(
            @RequestParam("file") MultipartFile file) throws IOException {

        byte[] bytes = file.getBytes();

        return CompletableFuture.supplyAsync(() -> {
            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setFlavor(MarkdownFlavor.GITHUB);

            try (InputStream stream = new java.io.ByteArrayInputStream(bytes);
                 MarkdownConverter converter = new MarkdownConverter(stream)) {

                DocumentConvertResult result = converter.convert(options);

                return ResponseEntity.ok()
                        .contentType(MediaType.valueOf("text/markdown"))
                        .body(result.getContent());
            } catch (IOException e) {
                throw new IllegalStateException(e);
            }
        });
    }
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
This example is not part of the runnable examples repository — it needs Spring Boot on the classpath, which the examples project does not depend on.
{{< /alert >}}
