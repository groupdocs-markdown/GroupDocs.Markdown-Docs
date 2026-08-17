---
id: load-a-file-of-a-specific-format
url: markdown/java/load-a-file-of-a-specific-format
title: Load a file of a specific format
weight: 3
description: "This example demonstrates how to load a file of some particular format."
keywords: load a file
productName: GroupDocs.Markdown for Java
hideChildren: False
---

By default, GroupDocs.Markdown detects the file format automatically from the file extension or stream content. When you want to skip auto-detection or the file extension is missing, specify the format explicitly using `LoadOptions`.

{{< tabs "load-specific-format">}}
{{< tab "LoadSpecificFormat.java" >}}
```java
import com.groupdocs.markdown.*;

public class LoadSpecificFormat {

    public static void main(String[] args) {
        // Explicitly specify the format to skip auto-detection
        LoadOptions loadOptions = new LoadOptions(FileFormat.XLSX);

        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx", loadOptions)) {
            converter.convert("load-specific-format.md");
        }
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-specific-format.md" >}}  
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
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-a-file-of-a-specific-format/LoadSpecificFormat/load-specific-format.md)
{{< /tab >}}
{{< /tabs >}}

### Available FileFormat values

The `FileFormat` enum includes the following values:

| Category | Values |
|---|---|
| Word Processing | `Doc`, `Docx`, `Docm`, `Dot`, `Dotx`, `Dotm`, `Rtf`, `Odt`, `Ott` |
| Spreadsheet | `Xlsx`, `Xls`, `Xlsb`, `Xlsm`, `Csv`, `Tsv`, `Ods`, `Ots` |
| PDF | `Pdf` |
| E-book | `Epub`, `Mobi` |
| Text | `Txt` |
| Help | `Chm` |

You can also retrieve supported formats programmatically:

{{< tabs "load-supported-formats">}}
{{< tab "LoadSupportedFormats.java" >}}
```java
import com.groupdocs.markdown.*;

import java.util.List;

public class LoadSupportedFormats {

    public static void main(String[] args) {
        List<FileFormat> formats = MarkdownConverter.getSupportedFormats();
        for (FileFormat fmt : formats) {
            System.out.println(fmt);
        }
    }
}
```
{{< /tab >}}
{{< tab "load-supported-formats.txt" >}}  
```text
DOC
DOCX
DOCM
DOT
DOTX
DOTM
RTF
ODT
OTT
XLSX
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-a-file-of-a-specific-format/LoadSupportedFormats/load-supported-formats.txt)
{{< /tab >}}
{{< /tabs >}}
