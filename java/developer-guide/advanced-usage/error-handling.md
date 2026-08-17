---
id: error-handling
url: markdown/java/error-handling
title: Error handling
weight: 7
description: "Handle conversion errors with specific exception types"
keywords: error handling, exceptions, password, format, error
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

All `convert()` methods throw on failure. Catch `GroupDocsMarkdownException` — it is the base type for everything the library raises:

{{< tabs "error-handling-example">}}
{{< tab "ErrorHandlingExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class ErrorHandlingExample {

    public static void main(String[] args) {
        try {
            MarkdownConverter.toFile("annual-report.docx", "error-handling-example.md");
        } catch (GroupDocsMarkdownException e) {
            System.out.println("Conversion failed: " + e.getMessage());
        }
    }
}
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling-example.md" >}}  
```text
![](data:...;base64,[elided])

**Annual Report 2025**

Meridian Outdoor Co.


# **Table of Contents**

Meridian Outdoor Co.	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/error-handling/ErrorHandlingExample/error-handling-example.md)
{{< /tab >}}
{{< /tabs >}}

### Exception types

| Exception | When thrown |
|---|---|
| `DocumentProtectedException` | Document is password-protected and no password or wrong password was provided |
| `InvalidFormatException` | File is corrupt or has an unrecognized format |
| `GroupDocsMarkdownException` | General conversion error |

All three are **unchecked** — they extend `RuntimeException`, so the compiler does not force you to catch or declare them. `DocumentProtectedException` and `InvalidFormatException` both extend `GroupDocsMarkdownException`.

{{< alert style="warning" >}}
**Catch the base type, not the subtypes.** In 26.5 the converter wraps the specific exception inside a `GroupDocsMarkdownException` rather than letting it propagate, so a `catch (DocumentProtectedException e)` block never runs — the wrapper carries the original type name in its message instead. Catch `GroupDocsMarkdownException` and inspect `getMessage()` to distinguish causes.
{{< /alert >}}

### Conversion warnings

Non-fatal issues are reported via `DocumentConvertResult.getWarnings()`:

{{< tabs "warnings-example">}}
{{< tab "WarningsExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class WarningsExample {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setMaxRows(10);

        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx")) {
            DocumentConvertResult result = converter.convert("warnings-example.md", options);

            for (String warning : result.getWarnings()) {
                System.out.println("Warning: " + warning);
            }
        }
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "warnings-example.md" >}}  
```text
## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
| Parts and materials | $1,325,000.00 | $1,480,000.00 | $1,620,000.00 |
| Manufacturing equipment | $900,500.00 | $980,000.00 | $1,050,000.00 |
| Warehousing | $420,000.00 | $510,000.00 | $590,000.00 |
| Shipping | $380,000.00 | $445,000.00 | $520,000.00 |
| Marketing | $250,000.00 | $340,000.00 | $480,000.00 |
| R&D | $180,000.00 | $230,000.00 | $310,000.00 |
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/error-handling/WarningsExample/warnings-example.md)
{{< /tab >}}
{{< /tabs >}}
