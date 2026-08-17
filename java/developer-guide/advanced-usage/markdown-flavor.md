---
id: markdown-flavor
url: markdown/java/markdown-flavor
title: Markdown flavor control
weight: 3
description: "Target GitHub Flavored Markdown or CommonMark output"
keywords: markdown flavor, GFM, CommonMark, tables
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

GroupDocs.Markdown supports two Markdown dialects. Call `setFlavor` on `DocumentConvertOptions` to control the output.

### GitHub Flavored Markdown (default)

GFM supports pipe tables, strikethrough text, and other extensions:

{{< tabs "flavor-gfm">}}
{{< tab "FlavorGfm.java" >}}
```java
import com.groupdocs.markdown.*;

public class FlavorGfm {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setFlavor(MarkdownFlavor.GITHUB);

        MarkdownConverter.toFile("business-plan.docx", "flavor-gfm.md", options);

        // Tables are rendered as:
        // | Column A | Column B |
        // | --- | --- |
        // | value1 | value2 |
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "flavor-gfm.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/markdown-flavor/FlavorGfm/flavor-gfm.md)
{{< /tab >}}
{{< /tabs >}}

### CommonMark

Strict CommonMark output. Tables are rendered as fenced code blocks since CommonMark has no native table syntax:

{{< tabs "flavor-commonmark">}}
{{< tab "FlavorCommonmark.java" >}}
```java
import com.groupdocs.markdown.*;

public class FlavorCommonmark {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setFlavor(MarkdownFlavor.COMMON_MARK);

        MarkdownConverter.toFile("business-plan.docx", "flavor-commonmark.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "flavor-commonmark.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/markdown-flavor/FlavorCommonmark/flavor-commonmark.md)
{{< /tab >}}
{{< /tabs >}}
