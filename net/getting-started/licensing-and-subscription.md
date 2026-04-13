---
id: licensing-and-subscription
url: markdown/net/licensing-and-subscription
title: Licensing
weight: 6
description: free markdown API version is available to evaluate the API which will be similar to licensed version but with few limitations.
keywords: free markdown, license, markdown, API
productName: GroupDocs.Markdown for .NET
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
You can find pricing information on the ["Pricing Information"](https://purchase.groupdocs.com/pricing/markdown/net) page.
{{< /alert >}}

After obtaining a license, you need to set it up. This section describes options for how this can be done and also comments on some common questions.

The license should be set:

- Only once per application domain.
- Before using any other GroupDocs.Markdown classes.

{{< alert style="info" >}}
The license can be set multiple times per app domain but we recommend doing it once since all calls after the first one will just waste processor time.
{{< /alert >}}

### Set License from File (Static Method)

The `License.Set()` static method is the simplest way to apply a license. You do not need to create a `License` instance.

{{< tabs "license-static-file" >}}
{{< tab "C#" >}}
```csharp
// Set the license using the static method
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");
```
{{< /tab >}}
{{< /tabs >}}

### Set License from File (Instance Method)

Alternatively, you can create a `License` instance and call `SetLicense()`:

{{< tabs "license-instance-file" >}}
{{< tab "C#" >}}
```csharp
string licensePath = "GroupDocs.Markdown.lic";
License license = new License();
license.SetLicense(licensePath);
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Static Method)

You can also apply a license from a stream using the static `License.Set()` method:

{{< tabs "license-static-stream" >}}
{{< tab "C#" >}}
```csharp
using (FileStream stream = File.OpenRead("GroupDocs.Markdown.lic"))
{
    License.Set(stream);
}
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Instance Method)

The following example shows how to set a license from a stream using the instance method:

{{< tabs "license-instance-stream" >}}
{{< tab "C#" >}}
```csharp
using (FileStream stream = File.OpenRead("GroupDocs.Markdown.lic"))
{
    License license = new License();
    license.SetLicense(stream);
}
```
{{< /tab >}}
{{< /tabs >}}

### Set Metered License

You can also set a [Metered](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/metered) license as an alternative to a license file. It is a usage-based licensing mechanism that is billed based on the API features consumed. For more details, please refer to the [Metered Licensing FAQ](https://purchase.groupdocs.com/faqs/licensing/metered) section.

Use the `Metered` class to set up metered licensing and query your consumption:

{{< tabs "license-metered" >}}
{{< tab "C#" >}}
```csharp
string publicKey = ""; // Your public license key
string privateKey = ""; // Your private license key

Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);

// Get amount (MB) consumed
decimal amountConsumed = Metered.GetConsumptionQuantity();
Console.WriteLine("Amount (MB) consumed: " + amountConsumed);

// Get count of credits consumed
decimal creditsConsumed = Metered.GetConsumptionCredit();
Console.WriteLine("Credits consumed: " + creditsConsumed);
```
{{< /tab >}}
{{< /tabs >}}
