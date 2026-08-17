---
id: export-spreadsheet
url: markdown/java/convert/export-spreadsheet
title: Xlsx to Md
weight: 3
description: "This article demonstrates how to convert Spreadsheet to Markdown with GroupDocs.Markdown for Java."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use GroupDocs.Markdown to convert XLSX and other spreadsheet files to Markdown tables. You can control how many columns and rows are included using spreadsheet-specific options.

### Using static method

The simplest way to convert a spreadsheet file:

{{< tabs "export-spreadsheet-static">}}
{{< tab "ExportSpreadsheetStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportSpreadsheetStatic {

    public static void main(String[] args) {
        // Set license (optional)
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        // Convert XLSX to Markdown string
        String markdown = MarkdownConverter.toMarkdown("cost-analysis.xlsx");

        // Or save directly to a file
        MarkdownConverter.toFile("cost-analysis.xlsx", "export-spreadsheet-static.md");
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet-static.md" >}}  
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
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/ExportSpreadsheetStatic/export-spreadsheet-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API. The `DocumentConvertOptions` class provides spreadsheet-specific setters such as `setMaxColumns` and `setMaxRows` to limit the size of the exported tables:

{{< tabs "export-spreadsheet-instance">}}
{{< tab "ExportSpreadsheetInstance.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportSpreadsheetInstance {

    public static void main(String[] args) {
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx")) {
            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setMaxColumns(10);
            options.setMaxRows(100);
            options.setHeadingLevelOffset(1);

            converter.convert("export-spreadsheet-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet-instance.md" >}}  
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
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/ExportSpreadsheetInstance/export-spreadsheet-instance.md)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/java/getting-started/supported-document-formats" >}}).
