---
id: mcp-troubleshooting-faq
url: markdown/mcp/troubleshooting-faq
title: Troubleshooting & FAQ
weight: 5
description: "Solutions to the most common GroupDocs.Markdown MCP server issues — server not appearing in the client, startup failures, missing native dependencies, and first-launch timeouts."
keywords: MCP server not showing up in Claude Desktop, Claude can't see MCP tools, MCP server failed to start, dnx command not found, libgdiplus not found error, convert PDF to Markdown AI, document to markdown MCP, RAG ingestion local, EPUB to markdown agent
productName: GroupDocs.Markdown MCP Server
toc: True
---

Solutions to the most common GroupDocs.Markdown MCP server issues — server not appearing in the client, startup failures, missing native dependencies, and first-launch timeouts.

{{< alert style="info" >}}
**Platform-specific troubleshooting:** runtime problems depend on which build you run. For the `dnx` runner, native graphics libraries, and the Docker channel, see [Troubleshooting (.NET)]({{< ref "markdown/net/mcp/troubleshooting.md" >}}). The issues on this page apply to every platform.
{{< /alert >}}

## Why is my MCP server not showing up in Claude Desktop?

1. **Restart the client** — every client reads its MCP config only at startup.
2. Check the config file location for your OS ([per-client reference]({{< ref "markdown/net/mcp/install-in-ai-clients.md" >}})) and that the entry sits under the right root key (`mcpServers` for Claude Desktop/Cursor/Windsurf, `servers` for VS Code/VS 2022).
3. Validate the JSON — a trailing comma silently breaks the whole file. If you used the [installer](https://github.com/groupdocs/GroupDocs.Mcp.Installer), a timestamped `.bak` of your previous config sits next to the file for comparison.

## The first tool call is slow or fails once, then works

A **cold cache**: on the very first use the server's package or image is still downloading while the client is already waiting on the connection. Warming it once fixes it for good — the exact command depends on your build: [.NET]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#the-first-tool-call-is-slow-or-fails-once-and-then-works).

## The server fails to start, or a runtime dependency is missing

These are properties of the build you run rather than of MCP, so the fixes live with the platform:

| Symptom | Where the fix is |
|---|---|
| `dnx: command not found` | [.NET troubleshooting]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#dnx-command-not-found) — `dnx` ships inside the .NET 10 SDK |
| `DllNotFoundException: libgdiplus` on Linux/macOS | [.NET troubleshooting]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#dllnotfoundexception-libgdiplus) — install the native graphics libraries, or use the Docker image |
| "docker daemon not reachable" | [.NET troubleshooting]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#docker-daemon-not-reachable) — start Docker Desktop or `dockerd` |

## The agent says a file does not exist

Pass the **file name**, not a full path from your machine: the server resolves names inside its configured storage folder. When a name is not found the tool responds with the list of files it can see, so the agent can correct itself — check that list against [`GROUPDOCS_MCP_STORAGE_PATH`]({{< ref "markdown/net/mcp/configuration.md" >}}).

## Why is my Markdown only three pages long?

Evaluation mode processes **only the first three pages**. This is the single most important thing to know about this server, because the output looks perfectly valid — it is simply missing almost everything. Check [`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}) before any ingestion run; see [Licensing]({{< ref "markdown/mcp/getting-started/licensing.md" >}}).

## Should images be base64 or files?

`images: "base64"` (the default) embeds pictures as data URIs, so the `.md` is self-contained — good for pasting into a chat or storing a single artefact. `images: "file"` writes them alongside the `.md` — much better for a repository or a RAG index, where a multi-megabyte data URI in the middle of a chunk is noise. There is also an option to skip images entirely when only the text matters.

## Is this the same as the Conversion server's Markdown output?

They overlap. [GroupDocs.Conversion](/conversion/mcp/) converts between 100+ formats, Markdown among them. This server is **specialised for Markdown**: it exposes the dialect (`github` or `commonmark`), image handling, page selection, and YAML front matter as first-class options. If Markdown is the destination and the details matter, use this one.

## Does it OCR scanned PDFs?

No. Conversion works on the text layer; a scanned, image-only PDF produces images rather than recognised text. The same is true across GroupDocs MCP servers — none of them include OCR today.

## What is front matter for?

`frontMatter: true` prepends YAML with title, author, format, and page count. Static site generators consume it directly, and RAG pipelines can use it as chunk metadata rather than re-deriving the source from a file path.

## Verifying an installation end-to-end

Ask your agent *"list your GroupDocs Markdown conversion tools and the license status"* — it should name `convert_to_markdown`, `get_document_info`, `get_license_status`. For a scripted check that performs the real MCP handshake and a live call through the engine, see [verifying a .NET installation]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#verifying-an-installation-end-to-end).

## Still stuck?

Post your config (redact license paths) and the client name in the [Markdown forum](https://forum.groupdocs.com/c/markdown/) — we answer MCP questions daily. Bugs: [GitHub issues](https://github.com/groupdocs-markdown/GroupDocs.Markdown.Mcp/issues).
