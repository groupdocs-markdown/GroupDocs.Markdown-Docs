---
id: get-document-info
url: markdown/java/get-document-info
title: Get document info
weight: 2
description: "Retrieve document metadata such as format, page count, title, and author without converting"
keywords: document info, metadata, page count, file format
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Use `getDocumentInfo()` or the static `getInfo()` method to retrieve document metadata without performing a full conversion. This is useful for building file browsers, validation pipelines, and pre-conversion UIs.

### Using static method

{{< tabs "get-info-static">}}
{{< tab "GetInfoStatic.java" >}}
```java
import com.groupdocs.markdown.*;

public class GetInfoStatic {

    public static void main(String[] args) {
        DocumentInfo info = MarkdownConverter.getInfo("business-plan.docx");

        System.out.println("Format:    " + info.getFileFormat());   // Docx
        System.out.println("Pages:     " + info.getPageCount());    // 42
        System.out.println("Title:     " + info.getTitle());        // "Q3 Report"
        System.out.println("Author:    " + info.getAuthor());       // "Jane Doe"
        System.out.println("Encrypted: " + info.isEncrypted());     // false
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-static.txt" >}}  
```text
Format:    DOCX
Pages:     5
Title:     Meridian Outdoor Co. — Business Plan
Author:    Meridian Outdoor Co.
Encrypted: false
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/get-document-info/GetInfoStatic/get-info-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance method

{{< tabs "get-info-instance">}}
{{< tab "GetInfoInstance.java" >}}
```java
import com.groupdocs.markdown.*;

public class GetInfoInstance {

    public static void main(String[] args) {
        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx")) {
            DocumentInfo info = converter.getDocumentInfo();

            System.out.println("Format:    " + info.getFileFormat());
            System.out.println("Pages:     " + info.getPageCount());
            System.out.println("Title:     " + info.getTitle());
            System.out.println("Author:    " + info.getAuthor());
            System.out.println("Encrypted: " + info.isEncrypted());
        }
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-instance.txt" >}}  
```text
Format:    XLSX
Pages:     4
Title:     
Author:    
Encrypted: false
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/get-document-info/GetInfoInstance/get-info-instance.txt)
{{< /tab >}}
{{< /tabs >}}

### DocumentInfo methods

| Method | Returns | Description |
|---|---|---|
| `getFileFormat()` | `FileFormat` | Detected file format (e.g., `FileFormat.DOCX`) |
| `getPageCount()` | `int` | Number of pages or worksheets |
| `getTitle()` | `String` | Document title from metadata |
| `getAuthor()` | `String` | Document author from metadata |
| `isEncrypted()` | `boolean` | Whether the document is password-protected |
