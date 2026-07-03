# Discord Quest Auto-Completer

Automatically synced mirror of [aamiaa's Discord Quest completion script](https://gist.github.com/aamiaa/204cd9d42013ded9faf646fae7f89fbb). A GitHub Actions workflow fetches the latest version from the gist every week and commits the extracted JavaScript file here — so you can always `curl` a clean `.js` file.

> [!CAUTION]
> Discord has expressed intent to crack down on automating quest completion. Use at your own risk.

## Quick Use

> [!NOTE]
> Discord's CSP blocks `fetch()` to external URLs, but you can bypass it by injecting a `<script>` tag.

**Paste this one-liner into the Discord DevTools console** (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd> → **Console**):

```js
var s=document.createElement('script');s.src='https://raw.githubusercontent.com/nameIess/Discord-Quest/main/quest-script.js';document.head.appendChild(s);
```

**Alternative — copy from browser:**

Open the [raw script](https://raw.githubusercontent.com/nameIess/Discord-Quest/main/quest-script.js) in a new browser tab, <kbd>Ctrl</kbd>+<kbd>A</kbd> → <kbd>Ctrl</kbd>+<kbd>C</kbd>, then paste into Discord console.

## How It Works

A [GitHub Actions workflow](.github/workflows/update-script.yml) runs on a weekly schedule (every Monday at midnight UTC) and can also be triggered manually:

1. **Downloads** the raw Markdown from the gist
2. **Extracts** the JavaScript code block using `sed`
3. **Commits** the result as `quest-script.js` — only if the content has changed

This keeps the script in sync with upstream without any manual effort.

## Manual Trigger

Go to **Actions** → **Update Quest Script from Gist** → **Run workflow** to pull the latest version on demand.

## Credits

All credit for the script goes to [**aamiaa**](https://github.com/aamiaa) — this repo is just an automated mirror.  
Original source: [gist.github.com/aamiaa/204cd9d42013ded9faf646fae7f89fbb](https://gist.github.com/aamiaa/204cd9d42013ded9faf646fae7f89fbb)

## License

The original script is licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html).
