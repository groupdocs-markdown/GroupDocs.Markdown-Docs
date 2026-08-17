---
id: image-file-strategy
url: markdown/java/image-file-strategy
title: Save image as file
weight: 2
description: "The listed articles below explain how to saves images to the file system during document conversion."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use `ExportImagesToFileSystemStrategy` to save images as separate files during conversion. The Markdown output will contain image references pointing to the exported files.

### Basic usage

{{< tabs "image-file-basic">}}
{{< tab "ImageFileBasic.java" >}}
```java
import com.groupdocs.markdown.*;

public class ImageFileBasic {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new ExportImagesToFileSystemStrategy("output/images"));

        MarkdownConverter.toFile("business-plan.pdf", "output/document.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-basic.zip" >}}  
```text
output/document.md (7 KB)
output/images/img-001.jpg (10 KB)
output/images/img-002.jpg (39 KB)
output/images/img-003.jpg (25 KB)
output/images/img-004.jpg (16 KB)
output/images/img-005.jpg (44 KB)
output/images/img-006.jpg (20 KB)
output/images/img-007.jpg (648 bytes)
output/images/img-008.jpg (48 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/ImageFileBasic/image-file-basic.zip)
{{< /tab >}}
{{< /tabs >}}

### Using a relative image path

By default, image references in the Markdown use the full images-folder path. Call `setImagesRelativePath` to produce portable, relative image links:

{{< tabs "image-file-relative">}}
{{< tab "ImageFileRelative.java" >}}
```java
import com.groupdocs.markdown.*;

public class ImageFileRelative {

    public static void main(String[] args) {
        ExportImagesToFileSystemStrategy strategy =
                new ExportImagesToFileSystemStrategy("output/images");
        strategy.setImagesRelativePath("images");

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(strategy);

        MarkdownConverter.toFile("business-plan.pdf", "output/document.md", options);

        // Markdown output contains: ![](images/img-001.png)
        // Image file saved to:     output/images/img-001.png
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-relative.zip" >}}  
```text
output/document.md (7 KB)
output/images/img-001.jpg (10 KB)
output/images/img-002.jpg (39 KB)
output/images/img-003.jpg (25 KB)
output/images/img-004.jpg (16 KB)
output/images/img-005.jpg (44 KB)
output/images/img-006.jpg (20 KB)
output/images/img-007.jpg (648 bytes)
output/images/img-008.jpg (48 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/ImageFileRelative/image-file-relative.zip)
{{< /tab >}}
{{< /tabs >}}
