---
id: spreadsheet-options
url: markdown/java/spreadsheet-options
title: Spreadsheet conversion options
weight: 6
description: "Control column truncation, row limits, sheet separators, and hidden worksheets"
keywords: spreadsheet, Excel, CSV, columns, rows, truncation, worksheets
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

When converting spreadsheets, use these setters on `DocumentConvertOptions` to control the Markdown table output.

### Column and row truncation

{{< tabs "spreadsheet-truncation">}}
{{< tab "SpreadsheetTruncation.java" >}}
```java
import com.groupdocs.markdown.*;

public class SpreadsheetTruncation {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setMaxColumns(8);   // Only first 8 columns
        options.setMaxRows(50);     // Only first 50 data rows per sheet

        MarkdownConverter.toFile("cost-analysis.xlsx", "spreadsheet-truncation.md", options);

        // Truncated columns/rows show "..." indicators.
        // Warnings are reported by DocumentConvertResult.getWarnings().
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "spreadsheet-truncation.md" >}}  
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
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/spreadsheet-options/SpreadsheetTruncation/spreadsheet-truncation.md)
{{< /tab >}}
{{< /tabs >}}

### Sheet separator and hidden sheets

{{< tabs "spreadsheet-sheets">}}
{{< tab "SpreadsheetSheets.java" >}}
```java
import com.groupdocs.markdown.*;

public class SpreadsheetSheets {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setSheetSeparator("\n---\n");     // Separator between worksheets
        options.setIncludeHiddenSheets(false);    // Skip hidden worksheets (default)

        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx")) {
            DocumentConvertResult result = converter.convert("spreadsheet-sheets.md", options);

            for (String warning : result.getWarnings()) {
                System.out.println("Warning: " + warning);
            }
            // e.g. "Worksheet 'Data' truncated at 50 rows."
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
{{< tab "spreadsheet-sheets.md" >}}  
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
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/spreadsheet-options/SpreadsheetSheets/spreadsheet-sheets.md)
{{< /tab >}}
{{< /tabs >}}

### Available options

| Setter | Type | Default | Description |
|---|---|---|---|
| `setMaxColumns` | `int` | `0` (unlimited) | Maximum columns per table |
| `setMaxRows` | `int` | `0` (unlimited) | Maximum data rows per worksheet |
| `setSheetSeparator` | `String` | `"\n---\n"` | Separator inserted between worksheets |
| `setIncludeHiddenSheets` | `boolean` | `false` | Whether to include hidden worksheets |
