---
id: features-overview
url: markdown/net/features-overview
title: Features overview
weight: 1
description: "Key features of GroupDocs.Markdown for .NET — document to Markdown conversion with flavor control, image handling, front matter, and more"
keywords: features, markdown, conversion, image export, front matter, heading offset, async
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Overview

GroupDocs.Markdown for .NET converts documents from various formats into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

## Supported Input Formats

Convert from 20+ document formats including Word (DOCX, DOC, RTF), Excel (XLSX, XLS, CSV), PDF, EPUB, MOBI, TXT, and CHM. See the full list of [supported formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}}).

## Key Features

### Static Convenience Methods

One-liner conversions that throw on failure — no result-checking ceremony:

{{< tabs "static-convenience-methods" >}}
{{< tab "C#" >}}
```csharp
string md = MarkdownConverter.ToMarkdown("document.docx");
MarkdownConverter.ToFile("document.docx", "output.md");
```
{{< /tab >}}
{{< /tabs >}}

### Markdown Flavor Control

Target GitHub Flavored Markdown (pipe tables, strikethrough) or strict CommonMark:

{{< tabs "markdown-flavor-control" >}}
{{< tab "C#" >}}
```csharp
var options = new ConvertOptions { Flavor = MarkdownFlavor.GitHub };
```
{{< /tab >}}
{{< /tabs >}}

### Flexible Image Handling

Choose how images are processed during conversion:
- **Base64 embedding** — images inline in the Markdown (default)
- **File system export** — save images to disk with relative paths
- **Skip** — omit images from the output
- **Custom** — rename, replace, or redirect images via callback

### YAML Front Matter

Extract document metadata into YAML front matter for static site generators (Jekyll, Hugo, Docusaurus):

{{< tabs "yaml-front-matter" >}}
{{< tab "C#" >}}
```csharp
var options = new ConvertOptions { IncludeFrontMatter = true };
```
{{< /tab >}}
{{< /tabs >}}

### Heading Level Offset

Shift all heading levels when embedding converted content inside a larger document:

{{< tabs "heading-level-offset" >}}
{{< tab "C#" >}}
```csharp
var options = new ConvertOptions { HeadingLevelOffset = 2 };
// # Title → ### Title
```
{{< /tab >}}
{{< /tabs >}}

### Spreadsheet Options

Control how Excel and CSV tables are rendered:
- Column and row truncation with ellipsis indicators
- Custom sheet separators
- Hidden worksheet filtering

### Document Inspection

Retrieve document metadata (format, page count, title, author) without performing a full conversion:

{{< tabs "document-inspection" >}}
{{< tab "C#" >}}
```csharp
DocumentInfo info = MarkdownConverter.GetInfo("report.docx");
```
{{< /tab >}}
{{< /tabs >}}

### Page Selection

Convert specific pages or worksheets instead of the full document:

{{< tabs "page-selection" >}}
{{< tab "C#" >}}
```csharp
var options = new ConvertOptions { PageNumbers = new[] { 1, 3, 5 } };
```
{{< /tab >}}
{{< /tabs >}}

### Relative Image Paths

Control how image file paths appear in the Markdown output:

{{< tabs "relative-image-paths" >}}
{{< tab "C#" >}}
```csharp
var strategy = new ExportImagesToFileSystemStrategy("output/images")
{
    ImagesRelativePath = "images"
};
```
{{< /tab >}}
{{< /tabs >}}

### Image Replacement

Replace images in the source document with different images during conversion using `IImageSavingHandler`.

### Async API

All static and instance methods have async counterparts with true async file I/O:

{{< tabs "async-api" >}}
{{< tab "C#" >}}
```csharp
string md = await MarkdownConverter.ToMarkdownAsync("document.docx");
```
{{< /tab >}}
{{< /tabs >}}

### Proper Error Handling

Specific exception types for common error scenarios:
- `DocumentProtectedException` — wrong or missing password
- `InvalidFormatException` — corrupt or unrecognized file
- `GroupDocsMarkdownException` — general conversion error

### Conversion Warnings

Non-fatal issues are reported via `ConvertResult.Warnings` — for example, when spreadsheet tables are truncated.

### Password-Protected Documents

Load encrypted documents by providing a password via `LoadOptions`:

{{< tabs "password-protected-documents" >}}
{{< tab "C#" >}}
```csharp
var loadOptions = new LoadOptions(FileFormat.Docx) { Password = "secret" };
```
{{< /tab >}}
{{< /tabs >}}

### Cross-Platform Support

Works on Windows, Linux, and macOS with .NET Framework 4.6.2+, .NET 6.0+, .NET 8.0+, and .NET 10.0+.
