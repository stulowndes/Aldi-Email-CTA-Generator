# Email CTA PNG Asset Generator

Standalone browser tool for generating CTA PNG assets from text lines. Each non-empty line becomes its own preview card, with per-asset controls for style and width, plus batch ZIP export.

## What It Does

- Generates PNG CTA assets directly in the browser
- Supports two styles: `Blue` and `White`
- Supports two widths:
  - `Normal`: `520x108`
  - `4-COL`: `284x108`
- Lets you change style and width per generated asset before download
- Downloads all generated assets as a single ZIP file
- Prevents filename collisions by suffixing duplicates with `_1`, `_2`, and so on
- Supports URL-driven generation for direct preview or asset rendering

## How To Use

1. Open [index.html](./index.html) in a browser.
2. Enter one CTA per line in the text area.
3. Choose the default style and default width for any new lines.
4. Review the generated preview cards.
5. Adjust style or width on individual cards if needed.
6. Click `Download ZIP` to export the full batch.

Each preview card also includes its own `Download PNG` button for single-asset export.

## URL Parameters

The app supports both single-asset and multi-asset input through query parameters.

### Single Asset

```text
?text=Hello%20World&style=Blue&size=Normal
```

Supported parameters:

- `text`: CTA copy
- `style`: `Blue` or `White`
- `size`: `Normal` or `4-COL`

### Multiple Assets

```text
?texts=First%0ASecond&styles=Blue,White&sizes=Normal,4-COL
```

Supported parameters:

- `texts`: newline-separated CTA values
- `styles`: comma- or newline-separated style values
- `sizes`: comma- or newline-separated size values

### Asset-Only View

```text
?text=Hello%20World&style=Blue&size=Normal&view=asset
```

When `view=asset` is present, the UI is hidden and only the first generated asset is rendered.

## File Naming

Downloads follow this format:

```text
CTA_your-text.png
```

Duplicate names are automatically renamed like this:

```text
CTA_your-text.png
CTA_your-text_1.png
CTA_your-text_2.png
```

## Technical Notes

- This is a single-file app with HTML, CSS, and JavaScript in [index.html](./index.html).
- ZIP export is handled directly in the browser with no external library dependency.
- No build step or install process is required.

## Run Locally

Because this is a static app, you can use either approach:

- Open [index.html](./index.html) directly in a browser
- Serve the folder with any simple static server if you prefer a local URL

## Limitations

- Long text is truncated with an ellipsis to fit the asset width
- Asset-only mode renders only the first generated asset