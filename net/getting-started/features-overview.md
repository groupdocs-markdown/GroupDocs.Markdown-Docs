---
id: features-overview
url: markdown/net/features-overview
title: Features overview
weight: 1
description: "Salient features of file markdown API using c# are described in this article"
keywords: file markdown
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## File markdown
This article describes the salient features of file markdown API using C#.

GroupDocs.Markdown main feature is the ability to convert any document from any of supported source document formats into Markdown file. (check the list of [supported formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}})). All these markdowns are possible without any additional software installed (like Microsoft Office, Apache Open Office, Adobe Acrobat Reader and others).
GroupDocs.Markdown provides a flexible set of settings to customize the markdown process to fulfill your needs:

### Convert specific document page(s)

Along with the whole document markdown to the desired target format, it could be useful to convert specific document pages or page ranges. For such partial document markdown, you should specify desired page numbers to convert using the [PageNumbers](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/pagenumbers/) property of the `DocumentConvertOptions` class.

### Auto-detect source document format

In some cases, the source file could be presented in a form of a byte stream, so the file extension is unknown.
Luckily GroupDocs.Markdown for .NET is smart enough to [detect source document format](({{< ref "markdown/net/developer-guide/advanced-usage/loading/" >}})) on the fly.

### Load source document with extended options

There are lots of modifications that are possible during the file markdown process:

- specify a password for [password-protected documents]({{< ref "markdown/net/developer-guide/advanced-usage/loading/load-a-password-protected-document.md" >}});