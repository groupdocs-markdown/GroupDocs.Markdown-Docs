---
id: mcp-uc-migrate-legacy-documentation
url: markdown/mcp/use-cases/migrate-legacy-documentation
title: How to migrate legacy documentation to Markdown with AI
linkTitle: Migrate legacy documentation
weight: 4
description: "Migrate legacy documentation archives — CHM help files, EPUB, old Word documents — to Markdown with an AI agent over MCP, locally and in bulk."
keywords: migrate documentation to markdown, CHM to markdown converter AI, legacy docs migration MCP, EPUB to markdown bulk
productName: GroupDocs.Markdown MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to migrate legacy documentation to Markdown with AI"
        description: "Migrate legacy documentation archives — CHM help files, EPUB, old Word documents — to Markdown with an AI agent over MCP, locally and in bulk."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Markdown MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Convert everything in the archive folder to Markdown with front matter and images as files. Report the source format, page count, and output size for each."
---

Internal documentation accumulates in whatever format was current when it was written: CHM help files, EPUB manuals, a decade of Word documents on a share. Markdown is where it should end up, and the conversion is one tool call per file.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The prompt

> Convert everything in the archive folder to Markdown with front matter and images as files. Report the source format, page count, and output size for each.

The agent loops the folder and calls [`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}}) per document. The report at the end is not decoration — it is how you spot the failures in a batch of four hundred.

## Formats that migrate well

* **DOCX / DOC / RTF / ODT** — structure is explicit in the source, so headings and tables come across cleanly.
* **EPUB / MOBI** — chapter structure maps naturally onto Markdown headings.
* **CHM** — old help files, still holding the only copy of some procedures.
* **XLSX** — worksheets become tables; useful for the parameter lists that documentation loves.

## The files that will not migrate

**Scanned PDFs.** A picture of a page has no text to convert, and this server has no OCR step. In a legacy archive these are usually a meaningful fraction — the documents someone scanned in 2009 because the original was lost.

Find them before the migration instead of after:

> List the PDFs whose conversion produced less than 2 KB of Markdown for more than 5 pages.

Those are your scans. Handle them separately — OCR elsewhere, or keep them as PDFs and index them by metadata.

## Do it in batches

Four hundred documents in one prompt is an unreviewable run. Twenty at a time, with a report each round, gives you a chance to fix the pattern before it is applied to everything — and keeps [metered usage]({{< ref "markdown/mcp/getting-started/licensing.md" >}}#metered-pay-per-use-licensing) predictable.

## Licence first, always

Three pages per document in evaluation mode. A migration run unlicensed produces four hundred plausible-looking stubs, and the discovery usually happens weeks later when someone searches for a procedure that is not there. [`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}) before the first batch.

## Why local matters for an archive

The archive is the whole corpus — every internal procedure, price list, and post-mortem in one folder. Uploading it to a conversion service to migrate it is a larger disclosure than any single document would be. Here it is read by a local process, and only what the agent says travels. See [On-premise architecture]({{< ref "markdown/mcp/use-cases/on-premise-markdown-conversion.md" >}}).
