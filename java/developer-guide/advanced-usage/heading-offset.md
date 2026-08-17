---
id: heading-offset
url: markdown/java/heading-offset
title: Heading level offset
weight: 5
description: "Shift all heading levels in the Markdown output"
keywords: heading, offset, heading level, embed
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Use `setHeadingLevelOffset` to shift all heading levels in the output by a fixed number. This is useful when embedding converted content inside a larger document where top-level headings are already in use.

### Example

{{< tabs "heading-offset-example">}}
{{< tab "HeadingOffsetExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class HeadingOffsetExample {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setHeadingLevelOffset(2);

        MarkdownConverter.toFile("annual-report.docx", "heading-offset-example.md", options);

        // Source: # Title     → Output: ### Title
        // Source: ## Section  → Output: #### Section
        // Heading levels are clamped to the range 1-6.
    }
}
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "heading-offset-example.md" >}}  
```text
![](data:...;base64,[elided])

**Annual Report 2025**

Meridian Outdoor Co.


### **Table of Contents**

Meridian Outdoor Co.	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/heading-offset/HeadingOffsetExample/heading-offset-example.md)
{{< /tab >}}
{{< /tabs >}}
