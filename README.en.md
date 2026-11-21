# vault-archive

[简体中文](README.md)

vault-archive is an Obsidian desktop plugin that moves older notes and their attachments into a separate vault while preserving the original folder structure.

[Download the plugin](https://github.com/FenchD/vault-archive/releases/latest)

## Why I built it

Years of notes and attachments made my Obsidian vault slow to sync across my phone and several computers. Keeping the whole vault on my phone also took up a lot of storage.

I wanted a smaller vault for everyday use and separate archive vaults for older material. A smaller active vault means less data to sync between devices. I can save space by syncing only the active vault to my phone. Whenever I need an old note, I can open the corresponding archive vault in Obsidian and find the note and its attachments in the original folder structure.

## Installation

The plugin supports Obsidian 1.5.0 or later on Windows and macOS desktop.

1. Download `vault-archive-2.3.1.zip` from [Releases](https://github.com/FenchD/vault-archive/releases/latest).
2. Unzip it and copy the entire `vault-archive` folder into `.obsidian/plugins/` inside **the source vault you want to archive from**. Create the `plugins` folder if needed. The resulting path should be `<source-vault>/.obsidian/plugins/vault-archive/main.js`.
3. Reopen the source vault and enable **vault-archive** under **Settings → Community plugins**.

To upgrade, finish any active archive job and disable the plugin. Replace the installed files with the ones from the new ZIP, keep `data.json` in place, and re-enable the plugin.

## Your first archive

1. Create or choose a separate archive folder. It can sit alongside the source vault, for example `Notes` and `NotesArchive`. Keep both folders outside each other.
2. Open **Settings → vault-archive** and click **Choose folder…** under **Archive vault**. By default, the plugin selects notes last modified more than two calendar years ago. You can set a different age in years or days.
3. Configure **Excluded folders** and **Excluded file types** as needed. The plugin automatically skips dot-prefixed folders such as `.obsidian` at every level.
4. Click **Open archive preview** or run **vault-archive: Archive notes (review plan first)** from the command palette. Review the notes, attachments, and conflicts, then click **Archive these files**. Back up your vaults before the first run, and pause sync and external edits during archiving.
5. Open the archive folder as a vault in Obsidian to browse your archived notes.

## What happens during archiving

- Archived Markdown notes and attachments keep their relative paths. Note text stays intact. Each linked note is evaluated independently against the archive rules.
- If a note staying in the source vault still uses an attachment, the plugin keeps a copy in each vault. Note links that now point across vaults may stop resolving locally. The archive report lists those links and any missing attachments.
- The plugin verifies the entire batch of archive copies before removing source files. Reports, recovery records, and backups of overwritten files are stored under `.vault-archive` in the archive vault. If a transfer is interrupted or a push fails, run **vault-archive: Resume archive or retry Git push** from the command palette.

## Optional settings

- **On startup** is off by default. Choose **Delayed preview** to review a plan when Obsidian opens, or **Delayed automatic archive** to archive eligible items without reviewing each run.
- Under **Advanced options**, turn on **Remove folders emptied by archiving** to clean up source folders left empty by the current batch. This setting is off by default.
- Before turning on **Commit and push after archiving**, make sure Git is available and the archive vault is the root of a clean Git working tree. Configure an upstream for its current branch, a commit author, and working push credentials.

## Free use and license

vault-archive is closed-source. All plugin features are free to use and require no plugin account. See the [license](LICENSE) and [third-party notices](THIRD-PARTY-NOTICES.txt).

## File access and network use

- The plugin reads notes and attachments in the source vault and writes them to the separate archive directory you choose. It verifies the archive copies before removing the original files. If folder cleanup is enabled, it removes source directories emptied by the current archive run.
- Archiving runs locally and the plugin collects no telemetry. If you enable Git push, the plugin calls your local Git executable to send the archive commit to the remote configured for the current branch of the archive repository.

## Feedback

If you run into a problem or have a feature request, open an issue or scan the WeChat QR code below to get in touch. I’ll use feedback and real archiving needs to guide future updates. [Open an issue](https://github.com/FenchD/vault-archive/issues)

<img src="assets/wechat-qr.png" alt="Author’s WeChat QR code" width="240">
