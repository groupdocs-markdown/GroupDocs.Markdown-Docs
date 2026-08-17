---
id: load-a-password-protected-document
url: markdown/java/load-a-password-protected-document
title: Load a password-protected document
weight: 4
description: "This example demonstrates how to load a password-protected document."
keywords: load a password-protected document
productName: GroupDocs.Markdown for Java
hideChildren: False
---

To open a password-protected document, create a `LoadOptions` instance with the file format and call `setPassword`.

{{< tabs "load-password-static">}}
{{< tab "LoadPasswordStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Paths;

public class LoadPasswordStatic {

    public static void main(String[] args) throws IOException {
        LoadOptions loadOptions = new LoadOptions(FileFormat.DOCX);
        loadOptions.setPassword("secret");

        // Static one-liner
        String markdown = MarkdownConverter.toMarkdown("protected.docx", loadOptions);
        Files.write(Paths.get("load-password-static.md"), markdown.getBytes(StandardCharsets.UTF_8));
    }
}
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-static.md" >}}  
```text
**Confidential Memo**

From: Meridian Outdoor Co. — Strategy Team

Date: 2026-01-15

Subject: FY2026 M&A Targets



[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/LoadPasswordStatic/load-password-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< alert style="warning" >}}
**Password-protected spreadsheets do not open in 26.5.** The example below is correct, but the library rejects a valid password on an encrypted XLSX with `Invalid password.` — the same file and password open normally in GroupDocs.Markdown for .NET. Password-protected Word documents (above) work. This is being tracked as a library defect; no verified output is published for this example until it is fixed.
{{< /alert >}}

{{< tabs "load-password-instance">}}
{{< tab "LoadPasswordInstance.java" >}}
```java
import com.groupdocs.markdown.*;

public class LoadPasswordInstance {

    public static void main(String[] args) {
        LoadOptions loadOptions = new LoadOptions(FileFormat.XLSX);
        loadOptions.setPassword("secret");

        try (MarkdownConverter converter = new MarkdownConverter("protected.xlsx", loadOptions)) {
            converter.convert("load-password-instance.md");
        }
    }
}
```
{{< /tab >}}
{{< tab "protected.xlsx" >}}  
{{< tab-text >}}
`protected.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/protected.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Handling incorrect passwords

If the password is missing or incorrect the conversion fails. Catch `GroupDocsMarkdownException` to display a user-friendly message — see [Error handling]({{< ref "markdown/java/developer-guide/advanced-usage/error-handling" >}}) for why the base type rather than `DocumentProtectedException`:

{{< tabs "load-password-exception">}}
{{< tab "LoadPasswordException.java" >}}
```java
import com.groupdocs.markdown.*;

public class LoadPasswordException {

    public static void main(String[] args) {
        try {
            String markdown = MarkdownConverter.toMarkdown("protected.docx");
        } catch (GroupDocsMarkdownException e) {
            System.out.println("Cannot open document: " + e.getMessage());
        }
    }
}
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-exception.txt" >}}  
```text
Cannot open document: com.groupdocs.markdown.DocumentProtectedException: The document password is incorrect.
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/LoadPasswordException/load-password-exception.txt)
{{< /tab >}}
{{< /tabs >}}
