---
id: convert-specific-pages
url: markdown/net/convert-specific-pages
title: Convert specific pages
weight: 4
description: "This article demonstrates how to convert specific document pages by page number using GroupDocs.Markdown for .NET API."
keywords: Convert page, Convert pages, Convert specific pages
productName: GroupDocs.Markdown for .NET
hideChildren: False
---
[**GroupDocs.Markdown**](https://products.groupdocs.com/markdown/net) also provides the feature to convert selected page number.

To convert specific pages, follow these steps:

1.   Create an instance of [MarkdownConverter](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter) class and pass source document path as a constructor parameter.
2.   Instantiate the appropriate [DocumentConverterOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) class.
3.   Set the [PageNumbers](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/pagenumbers/) property of the [DocumentConverterOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) instance to the list of desired page number to be converted.
4.   Call the [Convert](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter/convert/) method of [MarkdownConverter](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter) class instance and pass the filename of the converted document and the instance of [DocumentConverterOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) from the previous steps.

The following code snippet shows how to convert first and third pages from the source document:

```csharp
using (var converter = new MarkdownConverter("sample.docx"))
{
    var options = new DocumentConverterOptions
    {
        PageNumbers = new []{ 1, 3 }
    };
    converter.Convert("output.md", options);
}
```