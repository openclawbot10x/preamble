# Newly Created Skills

- **pdf_reader**: Extracts text from PDF files.
  - Usage: `exec /home/romeo/.npm-global/lib/node_modules/openclaw/skills/pdf_reader/run.sh <file_path>`
  - Requires `pdftotext` to be installed.
- **wacli_media_downloader**: Downloads media from WhatsApp chats using `wacli`.
  - Usage: `exec /home/romeo/.npm-global/lib/node_modules/openclaw/skills/wacli_media_downloader/run.sh --chat <chat_jid> --id <message_id>`
  - Requires `wacli` to be installed and accessible at `/home/romeo/.local/bin/wacli/dist/wacli`.
- **wacli_send_file**: Sends a file with an optional caption to a specific WhatsApp chat using `wacli`.
  - Usage: `exec /home/romeo/.npm-global/lib/node_modules/openclaw/skills/wacli_send_file/run.sh --to <chatJID> --file <path-to-file> --caption "<some_caption_text>"`
  - Requires `wacli` to be installed and accessible at `/home/romeo/.local/bin/wacli/dist/wacli`.
  - **Note:** Always prefer this skill for sending files to WhatsApp chats, as the direct `message` tool may not reliably deliver media.

# Email Workflow: Sending via Gmail with Browser Tool

To send an email using Gmail via the `browser` tool with `profile="openclaw"`:

1.  **Open Gmail:** `browser.open(action='open', profile='openclaw', targetUrl='https://gmail.com')`
2.  **Click Compose:** Snapshot the page to find the 'Compose' button (e.g., `ref=e90`), then `browser.act(kind='click', ref='e90')`.
3.  **Type Recipients:** Snapshot the compose window, then `browser.act(kind='type', ref='<to_field_ref>', text='recipient1@example.com, recipient2@example.com')`. (Note: `type` was more reliable than `fill` for Gmail fields).
    *   To field example ref: `e513`
4.  **Type Subject:** `browser.act(kind='type', ref='<subject_field_ref>', text='Your Subject Here')`.
    *   Subject field example ref: `e526`
5.  **Type Body:** `browser.act(kind='type', ref='<body_field_ref>', text='Your Email Body Here')`.
    *   Body field example ref: `e544`
6.  **Click Send:** `browser.act(kind='click', ref='<send_button_ref>')`.
    *   Send button example ref: `e553`

This workflow requires successful login to Gmail in the `openclaw` browser profile.

This section will help me remember and quickly utilize these new capabilities.

# Workspace File Management

- **Temporary Files (`tmp` directory):** All temporary files, or files not intended for Git backup, should be created, edited, and deleted within the `/tmp` directory. This directory is ignored by Git.
- **Important Files:** Files like `MEMORY.md`, `USER.md`, and other configuration/core files are located outside the `tmp` directory and *are* part of the Git backup.
- **Git Operations:** The user may ask me to perform Git push operations in the future.
