---
id: error-handling
url: markdown/python-net/error-handling
title: Error handling
weight: 7
description: "Handle conversion errors with specific exception types"
keywords: error handling, exceptions, password, format, error
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

All conversion methods raise exceptions on failure. Use standard try/except with specific exception types:

{{< tabs "error-handling-example">}}
{{< tab "error_handling_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter
from groupdocs.markdown import DocumentProtectedException, InvalidFormatException, GroupDocsMarkdownException

def error_handling_example():
    """Demonstrate error handling with specific exception types during conversion."""

    try:
        # Step 1: Attempt to convert the document
        MarkdownConverter.to_file("annual-report.docx", "error-handling.md")
    except DocumentProtectedException:
        # Step 2a: Handle password-protected documents
        print("Wrong or missing password.")
    except InvalidFormatException:
        # Step 2b: Handle corrupt or unsupported file formats
        print("File is corrupt or unsupported.")
    except GroupDocsMarkdownException as ex:
        # Step 2c: Handle any other conversion errors
        print(f"Conversion failed: {ex}")

if __name__ == "__main__":
    error_handling_example()
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling.txt" >}}  
{{< tab-text >}}
Output produced by this example ([download](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/error_handling_example/error-handling.txt)):
````
[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]


# Employee Information


| Job Title |  AUTOTEXTLIST  \t "<wr:out select='${varName1.Title}'/>" [Title] |
| --- | --- |
...
````
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling.txt" >}}  
{{< tab-text >}}
Output produced by this example ([download](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/error_handling_example/error-handling.txt)):
<pre><code>[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]


# Employee Information


| Job Title |  AUTOTEXTLIST  \t &quot;&lt;wr:out select='${varName1.Title}'/&gt;&quot; [Title] |
| --- | --- |
...</code></pre>
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling.txt" >}}  
```text
[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]


# Employee Information


| Job Title |  AUTOTEXTLIST  \t "<wr:out select='${varName1.Title}'/>" [Title] |
| --- | --- |
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/error_handling_example/error-handling.txt)
{{< /tab >}}
{{< tab "error-handling.txt" >}}  
```text
[queryEmployees]

Employee Information for Employee [EmployeeID]: [FirstName] [LastName]


# Employee Information


| **Job Title** | **[Title]** |
| --- | --- |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/error_handling_example/error-handling.txt)
{{< /tab >}}
{{< /tabs >}}

### Exception types

| Exception | When raised |
|---|---|
| `DocumentProtectedException` | Document is password-protected and no password or wrong password was provided |
| `InvalidFormatException` | File is corrupt or has an unrecognized format |
| `GroupDocsMarkdownException` | General conversion error |

### Conversion warnings

Non-fatal issues are reported via `ConvertResult.warnings`:

{{< tabs "warnings-example">}}
{{< tab "warnings_example.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions

def warnings_example():
    """Show how to inspect non-fatal conversion warnings after converting."""

    # Step 1: Open the spreadsheet with a context manager
    with MarkdownConverter("cost-analysis.xlsx") as converter:
        # Step 2: Configure row truncation
        options = ConvertOptions()
        options.max_rows = 10  # limit to first 10 data rows per sheet

        # Step 3: Convert using keyword argument for options
        result = converter.convert("warnings.md", convert_options=options)

        # Step 4: Inspect non-fatal warnings (e.g., truncation notices)
        for warning in result.warnings:
            print(f"Warning: {warning}")

if __name__ == "__main__":
    warnings_example()
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "warnings.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
...
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/warnings_example/warnings.txt)
{{< /tab >}}
{{< tab "warnings.txt" >}}  
```text
## Cost data and chart

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Cost Analysis |  |  |  |  |  |
|  |  | PARETO CHART |  |  |  |  |  |
|  |  | COST ANALYSIS |  |  |  |  | COST CENTER |
|  |  | Cost center | Annual cost  | Percent of total | Cumulative percent |  |  |
|  |  | Parts and materials | $1,325,000.00  | 31.17% | 31.17% |  |  |
|  |  | Manufacturing equipment | $900,500.00  | 21.19% | 52.36% |  |  |
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/developer-guide/advanced-usage/error-handling/warnings_example/warnings.txt)
{{< /tab >}}
{{< /tabs >}}
