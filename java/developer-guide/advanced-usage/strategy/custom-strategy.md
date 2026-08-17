---
id: custom-strategy
url: markdown/java/custom-strategy
title: Save image by custom strategy
weight: 4
description: "The listed articles below explain how to user control how images are saved when a document is saved to Markdown format."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use `CustomImagesStrategy` with the `IImageSavingHandler` interface for full control over how each image is saved during conversion. You can rename files, redirect output to a custom stream, or replace image content entirely.

### Rename images with IImageSavingHandler

`IImageSavingHandler` is a functional interface, so a stateless handler can be written as a lambda. This one keeps a running counter, so it is written as a named class:

{{< tabs "custom-strategy-rename">}}
{{< tab "CustomStrategyRename.java" >}}
```java
import com.groupdocs.markdown.*;
import com.groupdocs.markdown.imageexport.IImageSavingHandler;

public class CustomStrategyRename {

    // Implement the IImageSavingHandler interface
    static class RenameHandler implements IImageSavingHandler {

        private int index;

        @Override
        public void handle(CustomImageSavingArgs args) {
            args.setOutputImageFileName("img_" + index + "_" + args.getImageFileName());
            index++;
        }
    }

    public static void main(String[] args) {
        // Use the handler with CustomImagesStrategy
        RenameHandler handler = new RenameHandler();

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new CustomImagesStrategy("output/images", handler));

        MarkdownConverter.toFile("business-plan.docx", "output/document.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-rename.zip" >}}  
```text
output/document.md (5 KB)
output/images/img_0_img-001.png (4 KB)
output/images/img_1_img-002.jpg (41 KB)
output/images/img_2_img-003.png (14 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/CustomStrategyRename/custom-strategy-rename.zip)
{{< /tab >}}
{{< /tabs >}}

### Replace image content with setReplacementImage

Use `setReplacementImage` to substitute the original image with different content (e.g., a watermarked version or a placeholder):

{{< tabs "custom-strategy-replace">}}
{{< tab "CustomStrategyReplace.java" >}}
```java
import com.groupdocs.markdown.*;
import com.groupdocs.markdown.imageexport.IImageSavingHandler;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class CustomStrategyReplace {

    static class WatermarkHandler implements IImageSavingHandler {

        @Override
        public void handle(CustomImageSavingArgs args) {
            try {
                // Replace the original image with a custom placeholder
                InputStream placeholder = new FileInputStream("placeholder.png");
                args.setReplacementImage(placeholder);
                args.setOutputImageFileName("placeholder.png");
            } catch (IOException e) {
                throw new IllegalStateException("placeholder.png not found", e);
            }
        }
    }

    public static void main(String[] args) {
        WatermarkHandler handler = new WatermarkHandler();

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new CustomImagesStrategy("output/images", handler));

        MarkdownConverter.toFile("business-plan.docx", "output/document.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-replace.zip" >}}  
```text
output/document.md (5 KB)
output/images/placeholder.png (14 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/CustomStrategyReplace/custom-strategy-replace.zip)
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
Note the stream direction. `setReplacementImage` takes an **`InputStream`** -- the library *reads* your replacement bytes from it. `setOutputStream`, by contrast, takes an **`OutputStream`**, because the library *writes* the image into it. C# blurs this distinction behind a single `Stream` type; Java makes it explicit.
{{< /alert >}}
