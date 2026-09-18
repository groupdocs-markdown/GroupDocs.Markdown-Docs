---
id: mcp-uc-publish-to-a-static-site
url: markdown/mcp/use-cases/publish-to-a-static-site
title: How to publish documents to a static site as Markdown
linkTitle: Static-site publishing
weight: 2
description: "Turn documents into Markdown ready for Hugo, Jekyll, MkDocs, or Docusaurus with an AI agent over MCP, with YAML front matter and images as files."
keywords: documents to static site markdown, Hugo Jekyll markdown conversion AI, docs migration MCP, publish PDF as markdown
productName: GroupDocs.Markdown MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to publish documents to a static site as Markdown"
        description: "Turn documents into Markdown ready for Hugo, Jekyll, MkDocs, or Docusaurus with an AI agent over MCP, with YAML front matter and images as files."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Markdown MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Convert these documents to Markdown with front matter, GitHub flavour, and images saved as files."
---

Static site generators eat Markdown with YAML front matter and images on disk. That is exactly what [`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}}) produces when you ask for it.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The prompt

> Convert these documents to Markdown with front matter, GitHub flavour, and images saved as files.

Three options doing three jobs:

* `frontMatter: true` — YAML title, author, format, page count at the top. Hugo, Jekyll, MkDocs and Docusaurus all read it.
* `images: "file"` — pictures written alongside the `.md` and referenced by relative path, which is how a site expects them.
* `flavor: "github"` — GitHub-flavoured Markdown, the dialect most generators assume. Switch to `commonmark` if your toolchain is stricter.

## Fitting your generator's layout

The server writes files; arranging them is the agent's job:

> Put each converted file in a folder named after the document, with its images in an `images` subfolder next to it.

Most generators also want extra front-matter keys — `weight`, `menu`, `date`. Have the agent add them after conversion:

> Add `weight` to the front matter of each file, numbered in the order I listed them.

## Check before you publish

Two checks catch nearly everything:

* **Length against source.** A 60-page document producing 3 KB of Markdown means a scan or the [three-page evaluation limit]({{< ref "markdown/mcp/getting-started/licensing.md" >}}).
* **Images actually present.** Ask for a listing of the image folder; a `.md` referencing pictures that were never written renders as broken images on the site.

## Tables and structure

Word and Excel sources convert with their structure intact — headings become headings, tables become Markdown tables. PDFs vary with how they were produced: a born-digital export converts cleanly; a scan does not convert at all in any useful sense.

Spot-check the messiest source before running a batch of two hundred.

## Then the site build

At this point Markdown is Markdown — commit it, run your generator, and the documents are pages. The conversion stayed on your machine, which matters when the archive being published contains material that is public *after* review but not before.
