---
id: mcp-uc-on-premise-markdown-conversion
url: markdown/mcp/use-cases/on-premise-markdown-conversion
title: "Running GroupDocs MCP servers on-premise: architecture and security model"
linkTitle: On-premise deployment
weight: 5
description: "Run Markdown conversion for AI agents fully on-premise: local stdio transport, no external endpoints, no inbound ports, no telemetry."
keywords: on-premise MCP server, air-gapped markdown conversion, MCP security model, local RAG ingestion no upload
productName: GroupDocs.Markdown MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "Running GroupDocs MCP servers on-premise: architecture and security model"
        description: "Run Markdown conversion for AI agents fully on-premise: local stdio transport, no external endpoints, no inbound ports, no telemetry."
        steps:
        - name: "Run the pinned image inside the perimeter"
          text: "Start the GroupDocs.Markdown MCP server from its versioned Docker image as a child process of the AI client."
        - name: "Mount only the folders the agent may reach"
          text: "Map the document folder read-write and the license folder read-only."
        - name: "Choose the license mode"
          text: "Use a license file for fully offline operation; metered licensing needs outbound egress for usage reports."
---

Run Markdown conversion for AI agents **fully on-premise**: the GroupDocs.Markdown MCP server uses local stdio transport with **no external endpoints, no inbound ports, and no telemetry**. This page is the one to send your security reviewer.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The architecture in one picture

```text
+--------------+          +--------------------+         +------------------+
|  AI client   |  stdio   | MCP server process | reads / | local filesystem |
| (Claude, VS  | <----->  | (GroupDocs engine) | <-----> | storage / output |
| Code, agent) | JSON-RPC |   child process    |  writes |     folders      |
+--------------+          +--------------------+         +------------------+
```

* **Transport:** the AI client *starts the server as a child process* and communicates over standard input/output. The server never listens on a network socket.
* **Data path:** agent → local server → local filesystem. Sources and generated Markdown are read and written in the folders you configure; no document content is transmitted anywhere.
* **Network use:** only at install time (nuget.org or ghcr.io/docker.io). At runtime the server makes no outbound calls. Air-gapped: pre-pull the image or pre-cache the package and pin the version.
* **Telemetry:** none. The engine processes documents in-process.

## Ingestion is where corpora leak

Every RAG project faces the same moment: a folder containing everything the organisation knows has to be turned into text. Sending that folder to a hosted conversion API is the single largest disclosure in the pipeline, and it happens before anyone has thought about access control on the index.

Converting locally removes that step entirely. The corpus is read by a process on your machine; the Markdown lands next to it. What travels is the conversation — file names, page counts, and whatever the agent quotes back. With a locally-hosted model, nothing at all.

## Docker deployment inside the perimeter

```bash
docker run --rm -i \
  -v /srv/corpus:/data \
  -v /srv/licenses:/license:ro \
  -e GROUPDOCS_MCP_STORAGE_PATH=/data \
  -e GROUPDOCS_MCP_OUTPUT_PATH=/data/markdown \
  -e GROUPDOCS_LICENSE_PATH=/license/GroupDocs.Markdown.lic \
  ghcr.io/groupdocs-markdown/markdown-net-mcp:26.9.0
```

* Pin the tag (`:26.9.0`, not `:latest`).
* A separate output path keeps generated Markdown out of the source corpus.
* Licence read-only; mount only the folders the agent should reach.

## License management

* **License file** — read from local disk by the local process. Fully offline, and the only way to convert past page three.
* **Metered (pay-per-use)** — reports *usage* to GroupDocs servers, so it needs outbound egress. Document content is never part of that report.

Both are covered in [Licensing]({{< ref "markdown/mcp/getting-started/licensing.md" >}}).

## What this fits — honestly

**A good fit:** RAG and knowledge-base ingestion, documentation migration, publishing archives to a static site, and any of those inside a network that does not allow document uploads.

**Not what this is:** an OCR pipeline or a chunker. It converts documents that have a text layer into Markdown. Recognising text in scans, splitting into chunks, and embedding are separate steps you own.

## FAQ

**Does any document content leave the machine?** No. Conversion happens in-process against local files.

**Does it need internet at runtime?** No — only at install, and when metered licensing is enabled.

**Can I run it air-gapped?** Yes: pre-pull the image, use a license file, pin the version.

**What ports does it open?** None. stdio only.

**How do I prove that?** The [verification script]({{< ref "markdown/net/mcp/troubleshooting.md" >}}#verifying-an-installation-end-to-end) performs a real handshake and a real engine call so you can watch exactly what happens.
