---
{"dg-publish":true,"permalink":"/technology/homelab/git-hub-vrtmrzobsidian-livesync/","tags":["Obsidian","homelab"],"noteIcon":"","created":"2024-12-21 12:57:00 pm","updated":"2024-12-21 12:57:04 pm"}
---

instructions: https://jegtnes.com/blog/self-hosting-obsidian-sync-for-ios-android-mac-and-windows-with-couchdb/

# [GitHub - vrtmrz/obsidian-livesync](https://github.com/vrtmrz/obsidian-livesync)

## Self-hosted LiveSync

[Japanese docs](https://github.com/vrtmrz/obsidian-livesync/blob/main/README_ja.md) - [Chinese docs](https://github.com/vrtmrz/obsidian-livesync/blob/main/README_cn.md).

Self-hosted LiveSync is a community-implemented synchronization plugin, available on every obsidian-compatible platform and using CouchDB or Object Storage (e.g., MinIO, S3, R2, etc.) as the server.

[![obsidian_live_sync_demo](https://user-images.githubusercontent.com/45774780/137355323-f57a8b09-abf2-4501-836c-8cb7d2ff24a3.gif)](https://user-images.githubusercontent.com/45774780/137355323-f57a8b09-abf2-4501-836c-8cb7d2ff24a3.gif)

Note: This plugin cannot synchronise with the official "Obsidian Sync".

## Features

-   Synchronize vaults very efficiently with less traffic.
-   Good at conflicted modification.
    -   Automatic merging for simple conflicts.
-   Using OSS solution for the server.
    -   Compatible solutions can be used.
-   Supporting End-to-end encryption.
-   Synchronisation of settings, snippets, themes, and plug-ins, via [Customization sync(Beta)](https://github.com/vrtmrz/obsidian-livesync#customization-sync) or [Hidden File Sync](https://github.com/vrtmrz/obsidian-livesync#hiddenfilesync)
-   WebClip from [obsidian-livesync-webclip](https://chrome.google.com/webstore/detail/obsidian-livesync-webclip/jfpaflmpckblieefkegjncjoceapakdf)

This plug-in might be useful for researchers, engineers, and developers with a need to keep their notes fully self-hosted for security reasons. Or just anyone who would like the peace of mind of knowing that their notes are fully private.

Important

-   Before installing or upgrading this plug-in, please back your vault up.
-   Do not enable this plugin with another synchronization solution at the same time (including iCloud and Obsidian Sync).
-   This is a synchronization plugin. Not a backup solution. Do not rely on this for backup.

## How to use

### 3-minute setup - CouchDB on fly.io

**Recommended for beginners**

[![LiveSync Setup onto Fly.io SpeedRun 2024 using Google Colab](https://camo.githubusercontent.com/6bbc3cfe8e4d8a047004d843ee9b3e600f42a2676bd0e1dda32f056ecd294b44/68747470733a2f2f696d672e796f75747562652e636f6d2f76692f3773615f493138333258632f302e6a7067)](https://www.youtube.com/watch?v=7sa_I1832Xc)

1.  [Setup CouchDB on fly.io](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_flyio.md)
2.  Configure plug-in in [Quick Setup](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/quick_setup.md)

### Manually Setup

1.  Setup the server
    1.  [Setup CouchDB on fly.io](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_flyio.md)
    2.  [Setup your CouchDB](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_own_server.md)
2.  Configure plug-in in [Quick Setup](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/quick_setup.md)

Tip

Now, fly.io has become not free. Fortunately, even though there are some issues, we are still able to use IBM Cloudant. Here is [Setup IBM Cloudant](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_cloudant.md). It will be updated soon!

## Information in StatusBar

Synchronization status is shown in the status bar with the following icons.

-   Activity Indicator
    -   📲 Network request
-   Status
    -   ⏹️ Stopped
    -   💤 LiveSync enabled. Waiting for changes
    -   ⚡️ Synchronization in progress
    -   ⚠ An error occurred
-   Statistical indicator
    -   ↑ Uploaded chunks and metadata
    -   ↓ Downloaded chunks and metadata
-   Progress indicator
    -   📥 Unprocessed transferred items
    -   📄 Working database operation
    -   💾 Working write storage processes
    -   ⏳ Working read storage processes
    -   🛫 Pending read storage processes
    -   📬 Batched read storage processes
    -   ⚙️ Working or pending storage processes of hidden files
    -   🧩 Waiting chunks
    -   🔌 Working Customisation items (Configuration, snippets, and plug-ins)

To prevent file and database corruption, please wait to stop Obsidian until all progress indicators have disappeared as possible (The plugin will also try to resume, though). Especially in case of if you have deleted or renamed files.

## Tips and Troubleshooting

If you are having problems getting the plugin working see: [Tips and Troubleshooting](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/troubleshooting.md)

## License

Licensed under the MIT License.