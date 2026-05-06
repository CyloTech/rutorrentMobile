## ruTorrent Mobile (Appbox)

Mobile-friendly ruTorrent UI: touch targets, simplified navigation, and styling aligned with the [Appbox](https://appbox.co) dashboard (Tailwind-based surfaces, indigo accent, Appbox emblem in the header).

Maintained by **CyloTech** as a fork of [xombiemp/rutorrentMobile](https://github.com/xombiemp/rutorrentMobile).

### Requirements

- **httprpc** plugin (required).
- ruTorrent **5.x** / **jQuery 3**–compatible environments are supported (see `init.js` for compatibility shims).

### Installation

Place all plugin files in a directory named **`mobile`** under `rutorrent/plugins/`.

Clone this repository:

```bash
cd rutorrent/plugins
git clone https://github.com/CyloTech/rutorrentMobile.git mobile
```

> **Note:** The directory **must** be named `mobile` so assets and `mobile.css` resolve correctly.

> **Warning:** Not compatible with the **ipad** plugin.

### Styling (Tailwind)

- **`appbox.css`** is generated from `styles/appbox-input.css` with the Tailwind v4 CLI.
- After changing markup (`mobile.html`), `init.js` strings that introduce new utility classes, or `styles/appbox-input.css`, rebuild:

```bash
npm install
npm run build:css
```

Commit the updated **`appbox.css`** so servers using the plugin do not need Node.js.

Optional plugins that add behaviour (unchanged from upstream):

- **_getdir** — browse server directories when adding a torrent.
- **erasedata** — delete with data from the delete confirmation flow.
- **seedingtime** — Added / Finished fields in details.
- **ratio** — ratio group in details.
- **throttle** — channel in details.

### Configuration

Options at the top of **`init.js`**:

| Option | Default | Description |
|--------|---------|-------------|
| `plugin.enableAutodetect` | `true` | Auto-load on detected mobile browsers. |
| `plugin.tabletsDetect` | `true` | Treat tablets as mobile for autodetect. |
| `plugin.eraseWithDataDefault` | `false` | Default “delete with data” when ruTorrent’s delete confirmation is disabled. |
| `plugin.sort` | `'-addtime'` | Default torrent list sort (`name`, `-name`, `size`, …; prefix `-` for descending). |

### Usage

With **`plugin.enableAutodetect`**, the mobile UI loads on supported mobile user agents. On desktop, append **`?mobile=1`** to the ruTorrent URL to force the mobile UI.

### Troubleshooting

- Ensure **httprpc** is installed and enabled.
- Confirm the plugin path is **`plugins/mobile/`** and that **`appbox.css`** and **`mobile.css`** are present.
- Remove the **ipad** plugin if scrolling or layout breaks.
- Report issues: [https://github.com/CyloTech/rutorrentMobile/issues](https://github.com/CyloTech/rutorrentMobile/issues) (include device, OS, browser, and web server details).

### License

GPL-3.0 (see `LICENSE`).
