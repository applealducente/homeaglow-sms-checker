# SMS Macro Checker

A one-page tool for the Homeaglow sales team. Paste an SMS macro and it tells you whether the text is safe to send as plain SMS (GSM-7), gives you a fixed version to copy, and shows segments and cost per 1,000 sends.

It uses the same rules as the "SMS Macro checker" Google Sheet:

- **Safe?** (column B): flags characters that force Unicode (UCS-2), such as curly apostrophes, em and en dashes, bullets and emoji.
- **Fixed version** (column C): swaps or removes those characters, then squeezes repeated spaces like the sheet's `TRIM`. One addition: accented letters SMS can't send become the plain letter (María -> Maria) instead of being deleted.
- **Characters to fix, encoding, segments, segments saved and cost** (columns D to H). Cost uses $0.004 per segment.

## Modes

- **One message**: paste, check, copy.
- **Whole sheet**: paste a copied column of messages to check them all at once. When the page is opened inside Claude, it can also read column A and write the fixed versions into column C through the viewer's Google Sheets connection. That part is hidden everywhere else.

## Files

- `index.html`: the whole app (HTML, CSS and JavaScript, no build step).
- `homeaglow-logo.png`: header logo.

## Deploy

It's a static site. On Vercel, import the repository with framework preset **Other**, no build command and the repository root as the output directory. Every push to `main` redeploys.
