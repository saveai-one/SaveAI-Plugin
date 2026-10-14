# SaveAI

Save AI conversations as **PDF, Word, Markdown, TXT, JSON or long screenshots**, or sync them to Notion. SaveAI is a browser extension for 20 AI sites, including ChatGPT, Claude, Gemini, DeepSeek, Copilot, Grok, Kimi, Doubao and Qwen.

[Website](https://saveai.one) · [User guide](https://www.saveai.one/docs/) · [Feedback](https://www.saveai.one/feedback/)

**Install:** [Chrome](https://chromewebstore.google.com/detail/lkhaghcekfkickbdachbheceknpmofdk) · [Edge](https://microsoftedge.microsoft.com/addons/detail/ohgnnmliihahfpdeggnojlednaklbbce) · [Firefox](https://addons.mozilla.org/firefox/addon/save-ai-chats-to-pdf-word/)

<img src="docs/readme-images/saveai-on-chatgpt-en.jpg" alt="SaveAI open on a ChatGPT conversation with equations and a table" width="820">

## Why I built SaveAI

Hi, I'm **Jack**, the creator of SaveAI and a software engineer with a bit of a perfectionist streak.

SaveAI started with a need in my own work. I wanted to organize and keep my conversations with AI: code discussions, mathematical explanations and plans revised over several rounds. I wanted to find them again without searching across different websites.

The tools I tried never quite met that need. Some offered too few export formats; others lost equations or special characters. Some charged a fee, but paying did not necessarily solve those problems. I wanted files I could read and use without fixing them first.

Since I already build software for a living, I decided to make my own tool. I could shape the features around real needs and keep improving anything that felt awkward. The idea was to build something I would use myself, then share it for free with people who needed the same thing.

After launch, SaveAI received far more attention, support and thoughtful feedback than I had expected. I have read every review and email carefully. Your reports and examples helped me notice details I had missed and encouraged me to keep improving it. **Thank you for helping SaveAI become more useful to others.**

## Features

- Export conversations from 20 supported AI sites through one extension.
- Choose from six file formats, or sync selected content to an authorized Notion page or database.
- Save the whole conversation or select individual messages in the preview page.
- Export through the toolbar popup, buttons on the page or the browser context menu.
- Read with eight themes and adjust fonts, text size and content width.
- Customize PDF paper size, orientation, margins, outline, page numbers and footer.
- Search and revisit captured conversations in the extension sidebar.

SaveAI currently provides its export features for free. Regular file exports do not require an account.

## Choose your format

| Format | Best for | Output |
| --- | --- | --- |
| PDF | Sharing, printing and archiving | A document with a fixed layout |
| Word | Revising a plan or report | An editable `.docx` document |
| Markdown | Obsidian, note libraries and further editing | Portable text with headings, lists and code |
| TXT | Keeping just the text | A lightweight plain text file |
| JSON | Processing conversations with scripts | Structured conversation data |
| Long screenshot | Sharing a conversation visually | A long image of the conversation |

<img src="docs/readme-images/popup-en.jpg" alt="English SaveAI popup with six export formats, message selection and Notion sync" width="340">

## Get started

1. Install SaveAI for your browser and pin it to the toolbar.
2. Open a conversation on a supported AI site.
3. Click the SaveAI icon and choose a format under **One-Click Export**.
4. To keep only part of the conversation, open **Pick & Export**, select the messages you need and export the selection.

For long chats, check that earlier messages have loaded. Some AI sites display only part of a conversation at a time. Scroll up if needed, then check the preview message list before exporting.

Images and attachments can be included when the original site allows access and the selected format supports them.

## Screenshots

<details>
<summary>Message selection and export preview</summary>

Select messages on the left and review the conversation on the right.

<img src="docs/readme-images/preview-en.jpg" alt="English export preview with message selection, search, a table and code" width="900">

</details>

<details>
<summary>Code and table export examples</summary>

Examples from the SaveAI website showing indented code and a table with mathematical notation.

<img src="docs/readme-images/code-and-tables-en.jpg" alt="Exported Python code and a table of quadratic equations with English labels" width="900">

</details>

<details>
<summary>PDF settings</summary>

Choose a cloud or local PDF engine and adjust the document layout.

<img src="docs/readme-images/pdf-settings-en.jpg" alt="English PDF settings including rendering engine, paper size, margins, page numbers and outline" width="850">

</details>

<details>
<summary>Public share link export tool</summary>

The [website tool](https://www.saveai.one/tools/share-to-pdf/) can export supported public AI conversation links without installing the extension. For conversations that require sign-in to read, use the extension in your own browser session.

<img src="docs/readme-images/share-link-tool-en.jpg" alt="English SaveAI website tool with a public share link input and export format choices" width="900">

</details>

Screenshots are from the SaveAI website and extension user guide. Available controls may vary with the installed version.

## Privacy and data handling

- **Local file generation:** Word, Markdown, TXT, JSON and long screenshots are generated in your browser.
- **PDF rendering:** PDF uses the cloud engine by default, which uploads conversation content to the SaveAI server for rendering. Choose the local engine to generate the PDF on your device through the browser print dialog.
- **Conversation cache:** Captured conversations are stored in a local browser cache. You can adjust the retention period or clear the cache. Export important material separately for safekeeping.
- **Notion sync:** Selected content is sent to the Notion destination you have authorized.
- **Website share link tool:** The server retrieves supported public links to prepare the conversation for export.

See the [privacy policy](https://www.saveai.one/privacy/) for details.

## Build from source

SaveAI uses React, TypeScript and Manifest V3. The documented build environment is **Node.js 22.x** and **npm 10.x**.

```bash
npm ci
npm run build            # Chrome and Edge: dist/
npm run build:firefox    # Firefox: dist-firefox/
node scripts/package.mjs # Chrome package: releases/save-ai-<version>.zip
```

See [BUILD.md](BUILD.md) for the build pipeline and Firefox source archive instructions.

To load a local build:

- **Chrome or Edge:** Open `chrome://extensions` or `edge://extensions`, enable Developer mode, choose **Load unpacked** and select `dist/`.
- **Firefox:** Open `about:debugging`, choose **This Firefox**, then **Load Temporary Add-on** and select `dist-firefox/manifest.json`.

## Project structure

```text
src/
├── popup/          # Toolbar popup
├── options/        # Settings page
├── preview/        # Export preview and message selection
├── sidepanel/      # Conversation list and batch export
├── content-new/    # Site adapters and export controls on the page
├── inject-web/     # Bridge to the AI site's page context
├── background/     # Extension worker, routing and context menus
└── shared/         # Settings, localization and shared helpers
scripts/            # Build, packaging and regression checks
vendor/upstream/    # Static build inputs: manifest, locales and icons
```

## Development checks

```bash
npx tsc -b
node scripts/test-ui-regressions.mjs
node scripts/test-package-regressions.mjs
node scripts/test-usage-optout.mjs
```

## Feedback

If you find missing messages, formatting problems or a feature you would like to see, please send feedback through the [website](https://www.saveai.one/feedback/). I would also love to hear what you saved and how you plan to use it. Those details help me make SaveAI more useful in everyday work.
