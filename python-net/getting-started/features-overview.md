---
id: features-overview
url: markdown/python-net/features-overview
title: Features overview
weight: 1
description: "Key features of GroupDocs.Markdown for Python via .NET — document to Markdown conversion with flavor control, image handling, front matter, and more"
keywords: features, markdown, conversion, image export, front matter, heading offset, async, python
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

## Overview

GroupDocs.Markdown for Python via .NET converts documents from various formats into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

## Supported Input Formats

Convert from 30+ document formats including Word (DOCX, DOC, RTF), Excel (XLSX, XLS, CSV), PDF, EPUB, MOBI, TXT, and CHM. See the full list of [supported formats]({{< ref "markdown/python-net/getting-started/supported-document-formats.md" >}}).

## Key Features

### Static Convenience Methods

One-liner conversions that raise on failure — no result-checking ceremony:

```python
md = MarkdownConverter.to_markdown("business-plan.docx")
MarkdownConverter.to_file("business-plan.docx", "output.md")
```

### Markdown Flavor Control

Target GitHub Flavored Markdown (pipe tables, strikethrough) or strict CommonMark:

```python
options = ConvertOptions()
options.flavor = MarkdownFlavor.GIT_HUB
```

### Flexible Image Handling

Choose how images are processed during conversion:
- **Base64 embedding** — images inline in the Markdown (default)
- **File system export** — save images to disk with relative paths
- **Skip** — omit images from the output
- **Custom** — rename, replace, or redirect images via a Python callable

### YAML Front Matter

Extract document metadata into YAML front matter for static site generators (Jekyll, Hugo, Docusaurus):

```python
options = ConvertOptions()
options.include_front_matter = True
```

### Heading Level Offset

Shift all heading levels when embedding converted content inside a larger document:

```python
options = ConvertOptions()
options.heading_level_offset = 2
# # Title -> ### Title
```

### Spreadsheet Options

Control how Excel and CSV tables are rendered:
- Column and row truncation with ellipsis indicators
- Custom sheet separators
- Hidden worksheet filtering

### Document Inspection

Retrieve document metadata (format, page count, title, author) without performing a full conversion:

```python
info = MarkdownConverter.get_info("business-plan.docx")
```

### Page Selection

Convert specific pages or worksheets instead of the full document:

```python
options = ConvertOptions()
options.page_numbers = [1, 3, 5]
```

### Relative Image Paths

Control how image file paths appear in the Markdown output:

```python
strategy = ExportImagesToFileSystemStrategy("output/images")
strategy.images_relative_path = "images"
```

### Image Replacement

Replace images in the source document with different images during conversion using a custom image-saving handler.

### Async API

All static and instance methods have async counterparts with true async file I/O:

```python
md = await MarkdownConverter.to_markdown_async("business-plan.docx")
```

### Proper Error Handling

Specific exception types for common error scenarios:
- `DocumentProtectedException` — wrong or missing password
- `InvalidFormatException` — corrupt or unrecognized file
- `GroupDocsMarkdownException` — general conversion error

### Conversion Warnings

Non-fatal issues are reported via `ConvertResult.warnings` — for example, when spreadsheet tables are truncated.

### Password-Protected Documents

Load encrypted documents by providing a password via `LoadOptions`:

```python
load_options = LoadOptions(FileFormat.DOCX)
load_options.password = "secret"
```

### Cross-Platform Support

Works on Windows, Linux, and macOS with Python 3.5 or later (64-bit).
