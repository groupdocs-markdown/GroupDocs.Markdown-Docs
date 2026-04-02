---
id: strategy
url: markdown/net/strategy
title: Saving image strategy
weight: 11
description: ""
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

GroupDocs.Markdown provides several strategies for handling images during conversion. Set the `ImageExportStrategy` property on `ConvertOptions` to control the behavior:

* **Base64 embedding** -- inline images as data URIs using `ExportImagesAsBase64Strategy`.
* **File system export** -- save images to a directory using `ExportImagesToFileSystemStrategy`. Use the `ImagesRelativePath` property to control the relative path written into Markdown image links.
* **Skip images** -- omit all images from the output using `SkipImagesStrategy`.
* **Custom handler** -- implement `IImageSavingHandler` for full control over image saving, including renaming and custom storage via `CustomImagesStrategy`.

Please refer to the following guides for detailed examples:
