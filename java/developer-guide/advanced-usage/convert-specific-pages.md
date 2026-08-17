---
id: convert-specific-pages
url: markdown/java/convert-specific-pages
title: Convert specific pages
weight: 4
description: "This article demonstrates how to convert specific document pages by page number using GroupDocs.Markdown for Java API."
keywords: Convert page, Convert pages, Convert specific pages
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use the `setPageNumbers` method of `DocumentConvertOptions` to convert only selected pages (or worksheets) from the source document. Page numbering starts from 1.

### Using static method

{{< tabs "specific-pages-static">}}
{{< tab "SpecificPagesStatic.java" >}}
```java
import com.groupdocs.markdown.*;

public class SpecificPagesStatic {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setPageNumbers(new int[] { 1, 3 });

        // Convert only pages 1 and 3
        MarkdownConverter.toFile("business-plan.docx", "specific-pages-static.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-static.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **1. Executive Summary**

Meridian Outdoor Co. is a direct-to-consumer outdoor apparel and gear brand serving thru-hikers, backcountry travelers, and weekend adventurers. This plan outlines our strategy for fiscal year 2026, a year in which we expect to grow revenue by forty percent, expand into three new retail categories, and launch our sustainability certification program.
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesStatic/specific-pages-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "specific-pages-instance">}}
{{< tab "SpecificPagesInstance.java" >}}
```java
import com.groupdocs.markdown.*;

public class SpecificPagesInstance {

    public static void main(String[] args) {
        try (MarkdownConverter converter = new MarkdownConverter("business-plan.docx")) {
            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setPageNumbers(new int[] { 1, 3 });

            converter.convert("specific-pages-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-instance.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **1. Executive Summary**

Meridian Outdoor Co. is a direct-to-consumer outdoor apparel and gear brand serving thru-hikers, backcountry travelers, and weekend adventurers. This plan outlines our strategy for fiscal year 2026, a year in which we expect to grow revenue by forty percent, expand into three new retail categories, and launch our sustainability certification program.
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesInstance/specific-pages-instance.md)
{{< /tab >}}
{{< /tabs >}}

### Save specific pages to a file

{{< tabs "specific-pages-file">}}
{{< tab "SpecificPagesFile.java" >}}
```java
import com.groupdocs.markdown.*;

public class SpecificPagesFile {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setPageNumbers(new int[] { 2, 4, 5 });

        MarkdownConverter.toFile("business-plan.pdf", "specific-pages-file.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-file.md" >}}  
```text
**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1

FY2026StrategicPlan.................................................................................................................1

TableofContents.............................................................................................................................2

1.ExecutiveSummary..........................................................
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesFile/specific-pages-file.md)
{{< /tab >}}
{{< /tabs >}}
