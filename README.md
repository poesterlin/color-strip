# HTML Content Cleaner and Copier

This utility provides a web-based interface for cleaning HTML content pasted into an editor. It automatically removes specific formatting, such as inline style attributes and `<code>` tags, allowing users to copy the sanitized HTML markup to the clipboard.

## Features

- **Rich Text Pasting:** Accepts HTML content pasted into the designated editor area.
- **Automated Content Sanitization:**
  - Removes all inline `style="..."` attributes from pasted elements.
  - Removes `<code>` tags while preserving their inner text content.
- **HTML Clipboard Output:** Copies the processed content of the editor to the system clipboard as HTML, with a plain text fallback.
- **User Interface:** Provides a functional interface with visual feedback for copy operations.
- **Accessibility:** Incorporates basic accessibility features, including focus management and ARIA attributes.

## Usage Instructions

1.  **Copy Source Content:** Select and copy HTML content from an external source.
2.  **Paste into Editor:** Place the cursor within the editor field on the webpage and paste the copied content (e.g., using Ctrl+V or Cmd+V).
3.  **Processing:** The script automatically processes the pasted content upon insertion, removing specified attributes and tags.
4.  **Result:** The cleaned HTML markup is now available on the system clipboard for use elsewhere.

## Implementation Details

- The editor area is created using a `<div>` element with the `contenteditable="true"` attribute.
- A `paste` event listener triggers the cleaning process.
- `setTimeout(..., 0)` is used to defer the cleaning logic until after the browser's default paste handling completes and the DOM is updated.
- DOM manipulation methods (`querySelectorAll`, `removeAttribute`, `insertBefore`, `removeChild`/`remove()`) are employed to modify the pasted content directly within the editor.
- The `navigator.clipboard.write()` method, part of the asynchronous Clipboard API, is used to write both `text/html` and `text/plain` formats to the clipboard via a `ClipboardItem`.
