---
id: licensing-and-subscription
url: markdown/java/licensing-and-subscription
title: Licensing
weight: 6
description: free markdown API version is available to evaluate the API which will be similar to licensed version but with few limitations.
keywords: free markdown, license, markdown, API
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

Sometimes, to study the system better, you want to dive into the code as fast as possible. To make this easier, GroupDocs.Markdown offers a Free Trial and a 30-day Temporary License for evaluation and provides different purchase plans.

{{< alert style="info" >}}
Note that there are a number of general policies and practices that guide you on how to evaluate, properly license, and purchase our products. You can find them in the ["Purchase Policies and FAQ"](https://purchase.groupdocs.com/policies) section.
{{< /alert >}}

## Free Trial or Temporary License

You can try GroupDocs.Markdown without buying a license.

### Free Trial

The evaluation version is the same as the purchased one -- the evaluation version simply becomes licensed when you set the license. You can set the license in a number of ways that are described in the next sections of this article.

The evaluation version comes with the following limitations:

* Only the first 3 pages are processed.
* Documents with more than 3 pages are not supported.
* An evaluation watermark is placed at the top of each page.

### Temporary License

If you wish to test GroupDocs.Markdown without the limitations of the trial version, you can also request a 30-day Temporary License. For more details, see the ["Get a Temporary License"](https://purchase.groupdocs.com/temporary-license) page.

## How to Set a License

{{< alert style="info" >}}
You can find pricing information on the ["Pricing Information"](https://purchase.groupdocs.com/pricing/markdown/java) page.
{{< /alert >}}

After obtaining a license, you need to set it up. This section describes options for how this can be done and also comments on some common questions.

The license should be set:

- Only once per JVM (more precisely, once per class loader that loads the library).
- Before using any other GroupDocs.Markdown classes.

{{< alert style="info" >}}
The license can be set multiple times per JVM but we recommend doing it once since all calls after the first one will just waste processor time.
{{< /alert >}}

### Set License from File (Static Method)

The `License.set()` static method is the simplest way to apply a license. You do not need to create a `License` instance.

{{< tabs "license-static-file" >}}
{{< tab "LicenseStaticFile.java" >}}
```java
import com.groupdocs.markdown.License;

import java.io.File;

public class LicenseStaticFile {

    public static void main(String[] args) {
        // Set the license using the static method
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Set License from File (Instance Method)

Alternatively, you can create a `License` instance and call `setLicense()`:

{{< tabs "license-instance-file" >}}
{{< tab "LicenseInstanceFile.java" >}}
```java
import com.groupdocs.markdown.License;

public class LicenseInstanceFile {

    public static void main(String[] args) {
        String licensePath = "GroupDocs.Markdown.lic";

        License license = new License();
        license.setLicense(licensePath);
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Static Method)

You can also apply a license from an `InputStream` using the static `License.set()` method:

{{< tabs "license-static-stream" >}}
{{< tab "LicenseStaticStream.java" >}}
```java
import com.groupdocs.markdown.License;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class LicenseStaticStream {

    public static void main(String[] args) throws IOException {
        try (InputStream stream = new FileInputStream("GroupDocs.Markdown.lic")) {
            License.set(stream);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Instance Method)

The following example shows how to set a license from a stream using the instance method:

{{< tabs "license-instance-stream" >}}
{{< tab "LicenseInstanceStream.java" >}}
```java
import com.groupdocs.markdown.License;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

public class LicenseInstanceStream {

    public static void main(String[] args) throws IOException {
        try (InputStream stream = new FileInputStream("GroupDocs.Markdown.lic")) {
            License license = new License();
            license.setLicense(stream);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Set Metered License

You can also set a [Metered](https://reference.groupdocs.com/markdown/java/com.groupdocs.markdown/metered) license as an alternative to a license file. It is a usage-based licensing mechanism that is billed based on the API features consumed. For more details, please refer to the [Metered Licensing FAQ](https://purchase.groupdocs.com/faqs/licensing/metered) section.

Use the `Metered` class to set up metered licensing and query your consumption:

{{< tabs "license-metered" >}}
{{< tab "LicenseMetered.java" >}}
```java
import com.groupdocs.markdown.Metered;

public class LicenseMetered {

    public static void main(String[] args) {
        String publicKey = "";   // Your public license key
        String privateKey = "";  // Your private license key

        Metered metered = new Metered();
        metered.setMeteredKey(publicKey, privateKey);

        // Get amount (MB) consumed
        Double amountConsumed = Metered.getConsumptionQuantity();
        System.out.println("Amount (MB) consumed: " + amountConsumed);

        // Get count of credits consumed
        Double creditsConsumed = Metered.getConsumptionCredit();
        System.out.println("Credits consumed: " + creditsConsumed);
    }
}
```
{{< /tab >}}
{{< /tabs >}}
