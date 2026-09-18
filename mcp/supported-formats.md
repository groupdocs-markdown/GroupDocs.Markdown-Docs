---
id: mcp-supported-formats
url: markdown/mcp/supported-formats
title: Supported formats
weight: 4
description: "The MCP server exposes the full GroupDocs.Markdown engine: PDF, Word, Excel, EPUB, MOBI, CHM, CSV and 20+ more formats convert to clean Markdown."
keywords: MCP server supported formats, pdf to markdown MCP, epub to markdown, xlsx to markdown, docx to markdown agent
productName: GroupDocs.Markdown MCP Server
toc: True
---

The MCP server exposes the **full GroupDocs.Markdown engine**: every format the .NET library can turn into Markdown — 20+ document, spreadsheet, and e-book formats — is available to your AI agent through [`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}}). The canonical matrix lives in the library documentation: [supported document formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}}).

What each family gives you:

* **PDF** — the most common source, and the one where structure recovery matters: headings, lists, and tables come across rather than a wall of text.
* **DOCX / DOC / RTF / ODT** — the cleanest conversions, because the structure is already explicit in the source.
* **XLSX / XLS / ODS / CSV / TSV** — sheets become Markdown tables. `pages` selects **worksheets** here, not printed pages.
* **EPUB / MOBI / CHM** — e-books and help files, which is how a lot of internal documentation is still archived.
* **TXT** — normalised into Markdown with front matter if you ask for it.

**Scanned documents are the exception.** A PDF that is a picture of a page has no text layer, so the conversion produces images rather than prose. There is no OCR step here — check with [`get_document_info`]({{< ref "markdown/mcp/tools-reference/get-document-info.md" >}}) and your own eyes before feeding a scanned archive into an ingestion run.
