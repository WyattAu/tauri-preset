# tauri-preset

Shared Tauri v2 configuration presets for window, bundle, and security settings.

## Purpose

Provides a baseline `tauri.conf.json` preset that can be extended or merged into your own Tauri app configuration. Standardises window size, bundle targets, icons, and security defaults across projects.

## Preset defaults

| Setting | Value |
|---------|-------|
| Window size | 1200 × 800 |
| Window title | "Tauri App" |
| Resizable | true |
| Bundle targets | deb, rpm, msi, dmg, app, appimage, nsis |
| CSP | `default-src 'self'; img-src 'self' asset: https://asset.localhost; style-src 'self' 'unsafe-inline'` |

## Usage

### Option 1 — Extend via `$schema`

Point your `tauri.conf.json` at the preset and override only what you need:

```json
{
  "$schema": "./node_modules/tauri-preset/tauri-preset.json",
  "package": {
    "productName": "My App",
    "version": "1.0.0"
  },
  "windows": [
    {
      "title": "My App",
      "width": 900,
      "height": 600
    }
  ]
}
```

### Option 2 — Merge in build tooling

If your build tool supports JSON merge (e.g. `deepmerge` in JS):

```js
import preset from "tauri-preset/tauri-preset.json";

const config = deepmerge(preset, {
  package: { productName: "My App" },
});
```

## License

Licensed under either of [Apache License, Version 2.0](LICENSE-APACHE) or [MIT License](LICENSE-MIT) at your option.
