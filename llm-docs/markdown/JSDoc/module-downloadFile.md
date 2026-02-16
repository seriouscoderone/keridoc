# Module: downloadFile

This module downloads a file from a given URL and saves it to a specified path on the local file system.

##### Parameters:

| Name | Type | Description |
| --- | --- | --- |

| `downloadUrl` | string | The URL of the file to download. |
| `fullPath` | string | The full path of the file to write to. |

Source:

-   [modules-js-node/downloadFile.mjs](https://weboftrust.github.io/keridoc/JSDoc/modules-js-node_downloadFile.md), [line 11](https://weboftrust.github.io/keridoc/JSDoc/modules-js-node_downloadFile.md#line11)

##### Throws:

An error if the file cannot be downloaded.

Type

Error

##### Returns:

A Promise that resolves when the file is downloaded and written successfully.

Type

Promise.