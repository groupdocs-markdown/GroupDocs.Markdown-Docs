---
id: mcp-uc-convert-documents-for-rag
url: markdown/mcp/use-cases/convert-documents-for-rag
title: How to convert documents to Markdown for RAG with an AI agent
linkTitle: Convert documents for RAG
weight: 1
description: "Convert documents to clean Markdown for a RAG pipeline with an AI agent over MCP — locally, with image handling and front matter under your control."
keywords: convert documents for RAG, PDF to markdown ingestion AI, knowledge base ingestion MCP, local RAG document conversion
productName: GroupDocs.Markdown MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to convert documents to Markdown for RAG with an AI agent"
        description: "Convert documents to clean Markdown for a RAG pipeline with an AI agent over MCP — locally, with image handling and front matter under your control."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Markdown MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Before converting anything: what is the license status of the markdown server?"
---

Retrieval pipelines start with a conversion step, and that step decides how good the retrieval will be. Markdown is the format most chunkers and embedders handle best: headings survive, tables stay tables, lists stay lists.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The pattern

1. Put the corpus in the storage folder the server can see.
2. Ask: *"Convert every PDF in this folder to Markdown, images as files, with front matter."*
3. The agent calls [`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}}) per document.
4. `.md` files (and an image folder) land in your output folder, ready to chunk.

## Choose `images: "file"` for ingestion

The default embeds images as base64 data URIs, which makes a self-contained file — and makes a terrible RAG corpus: a single picture becomes a multi-megabyte blob sitting in the middle of a chunk, and your embedder gets a page of base64 instead of a paragraph of text.

For an index, use `images: "file"` (pictures written alongside, referenced by path) or skip images entirely when only the prose matters.

## Turn on front matter

`frontMatter: true` writes YAML with title, author, format, and page count at the top of each file. That is chunk metadata you would otherwise have to reconstruct from file names — and it lets a retrieval answer cite *"the Employee Handbook, page 42"* instead of *"handbook-final-v3.md"*.

## The trap that ruins ingestion runs

**Evaluation mode converts only the first three pages.** Nothing errors, nothing warns; you get a valid `.md` that contains the first three pages of a 200-page manual. Build an index from it and every retrieval quietly fails to find what it should.

Make the check the first step of any run:

> Before converting anything: what is the license status of the markdown server?

[`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}); see [Licensing]({{< ref "markdown/mcp/getting-started/licensing.md" >}}).

## Sanity-check the corpus, not just the tool

> For each converted file, tell me the source page count and the resulting Markdown length.

A 300-page manual that became 4 KB of Markdown is either a scan with no text layer or a truncated run. Both are invisible unless you look.

## Setup

```bash
dnx GroupDocs.Markdown.Mcp --yes
```

with `GROUPDOCS_MCP_STORAGE_PATH` pointing at the corpus — [per-client config]({{< ref "markdown/net/mcp/install-in-ai-clients.md" >}}) or the [installer]({{< ref "markdown/mcp/getting-started/_index.md" >}}).

## Where to go next

* [Publish documents to a static site]({{< ref "markdown/mcp/use-cases/publish-to-a-static-site.md" >}}) — front matter, images, and flavour.
* [Convert a section, not a book]({{< ref "markdown/mcp/use-cases/convert-a-section-not-a-book.md" >}}) — page ranges and worksheets.
* [Migrate legacy documentation]({{< ref "markdown/mcp/use-cases/migrate-legacy-documentation.md" >}}) — CHM, EPUB, and old Word archives.
* [On-premise architecture]({{< ref "markdown/mcp/use-cases/on-premise-markdown-conversion.md" >}}) — the corpus never leaves.
