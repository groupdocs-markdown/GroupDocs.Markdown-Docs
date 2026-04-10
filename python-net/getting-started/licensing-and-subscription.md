---
id: licensing-and-subscription
url: markdown/python-net/licensing-and-subscription
title: Licensing
weight: 6
description: free markdown API version is available to evaluate the API which will be similar to licensed version but with few limitations.
keywords: free markdown, license, markdown, API
productName: GroupDocs.Markdown for Python via .NET
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
You can find pricing information on the ["Pricing Information"](https://purchase.groupdocs.com/pricing/markdown/python-net) page.
{{< /alert >}}

After obtaining a license, you need to set it up. This section describes options for how this can be done and also comments on some common questions.

The license should be set:

- Only once per application domain.
- Before using any other GroupDocs.Markdown classes.

{{< alert style="info" >}}
The license can be set multiple times per app domain but we recommend doing it once since all calls after the first one will just waste processor time.
{{< /alert >}}

### Set License from File (Static Method)

The `License.set_()` static method is the simplest way to apply a license. You do not need to create a `License` instance.

{{< tabs "set-license-static">}}
{{< tab "set_license_static.py" >}}  
```python
import os
from groupdocs.markdown import License

def set_license_static():
    """Apply a license from a file using the static convenience method."""

    # Step 1: Set the license using the static method (call once per app)
    license_path = "GroupDocs.Markdown.lic"
    if os.path.exists(license_path):
        License.set_(license_path)

if __name__ == "__main__":
    set_license_static()
```
{{< /tab >}}
{{< /tabs >}}

### Set License from File (Instance Method)

Alternatively, you can create a `License` instance and call `set_license()`:

{{< tabs "set-license-instance">}}
{{< tab "set_license_instance.py" >}}  
```python
import os
from groupdocs.markdown import License

def set_license_instance():
    """Apply a license from a file using the instance method."""

    # Step 1: Define the path to the license file
    license_path = "GroupDocs.Markdown.lic"

    # Step 2: Create a License instance and apply the license
    if os.path.exists(license_path):
        license = License()
        license.set_license(license_path)

if __name__ == "__main__":
    set_license_instance()
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Static Method)

You can also apply a license from a stream using the static `License.set_()` method:

{{< tabs "set-license-stream-static">}}
{{< tab "set_license_stream_static.py" >}}  
```python
import os
from groupdocs.markdown import License

def set_license_stream_static():
    """Apply a license from a stream using the static convenience method."""

    # Step 1: Open the license file as a binary stream
    license_path = "GroupDocs.Markdown.lic"
    if os.path.exists(license_path):
        with open(license_path, "rb") as stream:
            # Step 2: Apply the license from the stream
            License.set_(stream)

if __name__ == "__main__":
    set_license_stream_static()
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Stream (Instance Method)

The following example shows how to set a license from a stream using the instance method:

{{< tabs "set-license-stream-instance">}}
{{< tab "set_license_stream_instance.py" >}}  
```python
import os
from groupdocs.markdown import License

def set_license_stream_instance():
    """Apply a license from a stream using the instance method."""

    # Step 1: Open the license file as a binary stream
    license_path = "GroupDocs.Markdown.lic"
    if os.path.exists(license_path):
        with open(license_path, "rb") as stream:
            # Step 2: Create a License instance and apply from the stream
            license = License()
            license.set_license(stream)

if __name__ == "__main__":
    set_license_stream_instance()
```
{{< /tab >}}
{{< /tabs >}}

### Set License from Environment Variable

You can auto-apply a license at import time by setting the `GROUPDOCS_LIC_PATH` environment variable. The license is applied automatically when the package is imported — no code changes needed:

```bash
export GROUPDOCS_LIC_PATH="path/to/GroupDocs.Markdown.lic"
```

The variable also accepts a URL if you serve the license from a license server:

```bash
export GROUPDOCS_LIC_PATH="https://license-server.example.com/api/license"
```

### Set Metered License

You can also set a [Metered](https://reference.groupdocs.com/markdown/python-net/groupdocs.markdown/metered) license as an alternative to a license file. It is a usage-based licensing mechanism that is billed based on the API features consumed. For more details, please refer to the [Metered Licensing FAQ](https://purchase.groupdocs.com/faqs/licensing/metered) section.

Use the `Metered` class to set up metered licensing and query your consumption:

{{< tabs "set-metered-license">}}
{{< tab "set_metered_license.py" >}}  
```python
from groupdocs.markdown import Metered

def set_metered_license():
    """Set up metered (usage-based) licensing and query consumption."""

    # Step 1: Provide your metered license keys
    public_key = ""   # your public license key
    private_key = ""  # your private license key

    # Step 2: Create a Metered instance and activate the keys (skip if keys not set)
    if public_key and private_key:
        metered = Metered()
        metered.set_metered_key(public_key, private_key)

        # Step 3: Query amount (MB) consumed
        amount_consumed = Metered.get_consumption_quantity()
        print("Amount (MB) consumed: " + str(amount_consumed))

        # Step 4: Query count of credits consumed
        credits_consumed = Metered.get_consumption_credit()
        print("Credits consumed: " + str(credits_consumed))

if __name__ == "__main__":
    set_metered_license()
```
{{< /tab >}}
{{< /tabs >}}
