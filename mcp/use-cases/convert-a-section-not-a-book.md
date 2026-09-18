---
id: mcp-uc-convert-a-section-not-a-book
url: markdown/mcp/use-cases/convert-a-section-not-a-book
title: How to convert just one section of a document to Markdown
linkTitle: Convert one section
weight: 3
description: "Convert only the pages or worksheets you need to Markdown with an AI agent over MCP, instead of processing an entire document."
keywords: convert specific pages to markdown, extract chapter as markdown AI, page range conversion MCP, worksheet to markdown
productName: GroupDocs.Markdown MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to convert just one section of a document to Markdown"
        description: "Convert only the pages or worksheets you need to Markdown with an AI agent over MCP, instead of processing an entire document."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Markdown MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Convert pages 40 to 52 of handbook.pdf to Markdown."
---

Most conversion requests are not about a whole book. They are about chapter 4, the appendix, or the one worksheet with the figures in it. The `pages` parameter keeps the work proportional.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The prompt

> Convert pages 40 to 52 of handbook.pdf to Markdown.

`pages` takes a comma-separated list of 1-based numbers — `"40,41,42"` and so on; an agent expands a range for you. Omit it and the whole document is converted.

## Find the numbers first

> How many pages does handbook.pdf have, and what is its title?

[`get_document_info`]({{< ref "markdown/mcp/tools-reference/get-document-info.md" >}}) answers before you commit to a long conversion, and catches an encrypted file up front rather than as a failure.

For "chapter 4" rather than "pages 40-52", you need the mapping: convert the table of contents pages first, read it, then ask for the range it names. Two small conversions instead of one enormous one.

## Spreadsheets address worksheets

In XLSX, XLS, and ODS the numbers select **worksheets**, not printed pages:

> Convert worksheet 2 of the model to Markdown.

That is how you get one table into a document without carrying the other fourteen sheets with it.

## Why bother, when you could convert everything?

* **Speed** — one chapter is a second; a 400-page manual with images is not.
* **Metered cost** — under [metered licensing]({{< ref "markdown/mcp/getting-started/licensing.md" >}}#metered-pay-per-use-licensing) you are billed for what you process.
* **Signal** — a RAG index with the one relevant appendix beats one with the entire back catalogue diluting every query.

## The evaluation-mode overlap

Unlicensed, only the first three pages are processed **regardless of what you ask for**. Requesting pages 40-52 unlicensed gets you pages 1-3, quietly. If the output does not start where you expected, that is the reason — [`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}).
