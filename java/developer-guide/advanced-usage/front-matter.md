---
id: front-matter
url: markdown/java/front-matter
title: YAML front matter
weight: 4
description: "Generate YAML front matter from document metadata for static site generators"
keywords: front matter, YAML, Jekyll, Hugo, Docusaurus, metadata
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Call `setIncludeFrontMatter(true)` to extract document metadata into a YAML block at the beginning of the Markdown output. This is commonly used by static site generators like Jekyll, Hugo, and Docusaurus.

### Example

{{< tabs "front-matter-example">}}
{{< tab "FrontMatterExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class FrontMatterExample {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setIncludeFrontMatter(true);

        MarkdownConverter.toFile("business-plan.docx", "front-matter-example.md", options);
        // Output:
        // ---
        // title: "Q3 Report"
        // author: "Jane Doe"
        // format: Docx
        // pages: 12
        // ---
        //
        // # Q3 Report
        // ...
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter-example.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Business Plan"
author: "Meridian Outdoor Co."
format: DOCX
pages: 5
---

![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/front-matter/FrontMatterExample/front-matter-example.md)
{{< /tab >}}
{{< /tabs >}}

### Combined with heading offset

{{< tabs "front-matter-combined">}}
{{< tab "FrontMatterCombined.java" >}}
```java
import com.groupdocs.markdown.*;

public class FrontMatterCombined {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setIncludeFrontMatter(true);
        options.setHeadingLevelOffset(1);

        MarkdownConverter.toFile("annual-report.docx", "front-matter-combined.md", options);
    }
}
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter-combined.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Annual Report 2025"
author: "Elena Márquez, CFO"
format: DOCX
pages: 6
---

![](data:...;base64,[elided])

**Annual Report 2025**
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/front-matter/FrontMatterCombined/front-matter-combined.md)
{{< /tab >}}
{{< /tabs >}}

### Front matter fields

Only non-empty fields are included:

| Field | Source | Example |
|---|---|---|
| `title` | Built-in document title property | `"Q3 Report"` |
| `author` | Built-in document author property | `"Jane Doe"` |
| `format` | Detected file format | `Docx` |
| `pages` | Page or worksheet count | `12` |
