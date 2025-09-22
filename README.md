# [Homepage](https://home.sarve.sh)

Minimal, fast, keyboard-friendly personal start page with customizable bookmarks and background.

![homepage](https://i.redd.it/cbnzq36zj3601.gif)

## Features

- **Bookmarks from defaults or your own JSON**: Ships with `bookmarks.js` and can be overridden via localStorage by uploading a JSON template.
- **Bottom-right settings menu**: A subtle gear reveals actions with a smooth animation.
- **Background editor**: Quickly set a solid color (hex picker) or upload an image (stored locally) as the background.
- **Keyboard-centric search**: Press Space to open search, Enter to search, Esc to close.
- **Clean, responsive layout**: Works well on desktop and mobile.

## Quick start

- Open `index.html` in a browser, or host the folder with any static server (e.g., GitHub Pages). A `CNAME` is included for the live instance.

## Customization

### 1) Bookmarks

- Default bookmark data lives in `bookmarks.js` as a global `bookmarks` array of sections: each section has a `title` and a `links` array with `{ name, url }`.
- For best visual balance with the current theme, keep exactly 4 sections, or adjust CSS (see note below).

JSON structure example:

```json
[
  {
    "title": "Feeds",
    "links": [
      { "name": "GitHub", "url": "https://github.com/explore" },
      { "name": "Hacker News", "url": "https://news.ycombinator.com" }
    ]
  },
  {
    "title": "Practice",
    "links": [
      { "name": "LeetCode", "url": "https://leetcode.com" }
    ]
  }
]
```

Note: The current styling assumes 4 sections. If you add more, tweak `.bookmark-set` sizing in `styles.css`.

#### Override bookmarks without editing code

Use the gear menu (bottom-right):

- Download template: saves the current default as `bookmarks-template.json`.
- Upload JSON: select your edited template to replace bookmarks (stored in localStorage).
- Reset to default: clears the override and restores `bookmarks.js`.

Validation ensures the uploaded JSON is an array of sections with `title` and `links` (`name`, `url`).

### 2) Background

Open the gear menu and click the palette icon:

- Choose a color: uses the native hex color picker and applies it immediately.
- Or choose an image: uploads from your device and sets it as a fixed, cover background.
- Background choices persist in localStorage and can be cleared via Reset.

### 3) Search engine

Edit `index.html` and change the value of `searchUrl` to your preferred engine.

Examples:

- Google: `https://google.com/search?q=`
- Bing: `https://www.bing.com/search?q=`
- DuckDuckGo: `https://duckduckgo.com/?q=`

### 4) Styling (CSS variables)

Edit the variables in `styles.css` under `:root` to re-theme the page.

| Variable           | default                    | description                                                                                                                |
| ------------------ | -------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `--bg`             | `#5f4b8b`                  | Body background color (overridden if a custom background is set via the palette)                                           |
| `--fg`             | `#ffffff`                  | Primary text color for clock and titles                                                                                    |
| `--secondaryFg`    | `#b3b3b3`                  | Link text color                                                                                                            |
| `--containerBg`    | `#272727`                  | Background color of the bookmark boxes                                                                                     |
| `--searchBg`       | `--containerBg`            | Background color of the search overlay                                                                                     |
| `--scrollbarColor` | `#3f3f3f`                  | Custom scrollbar color                                                                                                     |
| `--fontFamily`     | `"Roboto Mono", monospace` | Page font (import your own if you change this)                                                                             |

## Controls and shortcuts

- **Space**: Open search overlay
- **Esc**: Close search overlay
- **Enter**: Search current query
- **Bottom-right gear**: Toggle the settings menu
  - Palette: change background color or upload an image
  - Download template: export default bookmarks JSON
  - Upload JSON: import your bookmarks JSON
  - Reset: clear custom bookmarks and background

## Data persistence (localStorage)

- `customBookmarks`: JSON for user-uploaded bookmarks (overrides `bookmarks.js`)
- `customBackground`: JSON for background choice `{ color?: string, imageDataUrl?: string }`

All customization remains on the device in the browser’s localStorage.

## Developing

- Pure static site: no build required. Edit files and refresh.
- Host anywhere that serves static files (GitHub Pages, Netlify, Vercel, nginx, etc.).

## License

See `LICENSE`.
