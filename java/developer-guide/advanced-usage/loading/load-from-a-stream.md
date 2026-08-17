---
id: load-from-a-stream
url: markdown/java/load-from-a-stream
title: Load from a stream
weight: 2
description: "This example demonstrates how to load a file from a stream."
keywords: load a file from a stream
productName: GroupDocs.Markdown for Java
hideChildren: False
---

When the source document is not a file on disk (e.g., downloaded from a network, read from a database, or received as an upload), you can pass an `InputStream` directly to the `MarkdownConverter` constructor.

The stream is copied internally, so you may close it immediately after creating the converter. A multi-resource try-with-resources block closes both in the right order:

{{< tabs "load-stream-example">}}
{{< tab "LoadStreamExample.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class LoadStreamExample {

    public static void main(String[] args) throws IOException {
        try (InputStream stream = new FileInputStream("business-plan.docx");
             MarkdownConverter converter = new MarkdownConverter(stream)) {

            converter.convert("load-stream-example.md");
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-stream-example.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/LoadStreamExample/load-stream-example.md)
{{< /tab >}}
{{< /tabs >}}

### Stream with LoadOptions

If the stream does not have a file extension for automatic format detection, specify the format explicitly via `LoadOptions`:

{{< tabs "load-stream-options">}}
{{< tab "LoadStreamOptions.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class LoadStreamOptions {

    public static void main(String[] args) throws IOException {
        LoadOptions loadOptions = new LoadOptions(FileFormat.DOCX);

        try (InputStream stream = new FileInputStream("document");
             MarkdownConverter converter = new MarkdownConverter(stream, loadOptions)) {

            converter.convert("load-stream-options.md");
        }
    }
}
```
{{< /tab >}}
{{< tab "load-stream-options.md" >}}  
```text
| ![Woman with laptop and business documents](data:...;base64,[elided])**HOME BASED** |  |  |
| --- | --- | --- |
|  |  |  |
| **PROFESSIONAL SERVICES** |  |  |
|  | ***Business Plan*** |  |



- Introduction
- 1.	Executive Summary
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/LoadStreamOptions/load-stream-options.md)
{{< /tab >}}
{{< /tabs >}}
