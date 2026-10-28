# Suliworld

A warm, editorial theme for [Obsidian](https://obsidian.md), based on the design of [suliworld.com](https://www.suliworld.com): cream paper, forest green, a touch of orange, and serif accents.

> [!TIP]
> **Companion plugin: [Suliworld Signifiers](https://github.com/sulistef/obsidian-suliworld-signifiers)**
>
> The theme handles the overall appearance. The companion plugin defines, draws and manages bullet journal signifiers, including their symbols, colors, size and interactions. Configure them in Settings → Suliworld Signifiers.

![Suliworld, light mode (Cream)](images/cream.png)

## Features

- **Two light variants.** *Cream* (white sidebars, pill tabs) and *Forest* (deep green ribbon and sidebars, orange-underlined tabs).
- **Dark mode with floating cards.** Rounded panes float on a near-black canvas (desktop only).
- **Editorial headings.** Each level has its own look: a large light H1 with an optional divider, an orange mark before H2, forest green H3, a peach chip for H4, an orange dash for H5, and small caps for H6.
- **Accent titles.** Italic text inside a heading is set in the display serif, in orange:
  `# Slow software. *Why patience ships better apps*`
- **Tinted callouts.** Note in blue, tip in mint, warning in peach, question in lavender, quote in yellow.
- **Peach blockquotes** in the display serif, **dark code blocks** in iA Writer Duo, and embedded notes shown as a dark green card.
- **Pill highlights.** `==Highlighted text==` sits in a rounded pill with room around the words, in a warm yellow (deep ochre in dark mode). A highlight that wraps gets one pill per line.
- **Folder colors.** Each folder in the file explorer gets a colored mark and a tinted guide line, automatically or by folder name (see below).
- **Five font pairings**, all bundled: no network access is needed.
- **Mobile-friendly.** Heading sizes scale down on phones.

| Forest variant | Dark mode |
| --- | --- |
| ![Forest variant](images/forest.png) | ![Dark mode](images/dark.png) |

## Video

A tour of Cream, Forest and Night: warm paper, editorial headings, bundled fonts and note styles.

[![Watch Suliworld: A Warm, Editorial Theme for Obsidian on YouTube](images/video.jpg)](https://www.youtube.com/watch?v=1fKEe4P7Bpg)

## Installation

1. In Obsidian, open **Settings → Appearance → Themes → Manage**.
2. Search for **Suliworld** and select **Install and use**.
3. For the optional appearance controls, install [Style Settings](https://github.com/mgmeyers/obsidian-style-settings) and open its **Suliworld** section.

For manual installation, download `theme.css` and `manifest.json` from the [latest release](https://github.com/sulistef/obsidian-suliworld/releases/latest), place them in `.obsidian/themes/Suliworld/` inside your vault, and select Suliworld in Appearance.

## Companion plugin: Suliworld Signifiers

[Suliworld Signifiers](https://github.com/sulistef/obsidian-suliworld-signifiers) defines and draws bullet journal signifiers and manages their interactions. Install it from **Settings → Community plugins → Browse**, then search for **Suliworld Signifiers**. [Watch the plugin video](https://www.youtube.com/watch?v=4Ah9uRSWrIY).

Configure the Markdown characters, names, symbols, light/dark colors and size in **Settings → Suliworld Signifiers**. The plugin also provides the picker menu, suggestions, Enter behavior and commands, and works with any theme.

Suliworld handles the overall appearance: fonts, palette, layout and general note styles. It leaves task checkboxes standard when the plugin is disabled. Style Settings remains available for the theme’s general options; signifiers no longer require it. Existing signifier customizations saved by Style Settings are imported once by the updated plugin. Update Suliworld Signifiers to **1.1.0 or later before updating the theme to 1.0.3** so the plugin can import them.

## Folder colors

Folders show a small colored mark before their name, and the guide line under an open folder takes the same tint. Subfolders inherit their parent's color, a little lighter. The colors adapt to each variant: deeper on the white Cream sidebar, lighter on the Forest sidebar and in dark mode.

By default, top-level folders take the theme tints in turn: mint, lavender, orange, blue, yellow. To pick a color by folder name instead, add a CSS snippet (Settings → Appearance → CSS snippets) such as:

```css
.nav-folder:has(> .nav-folder-title:is([data-path="Projects"], [data-path="Archive"])) {
    --sw-folder-mark: "";
}

.nav-folder:has(> .nav-folder-title[data-path="Projects"]) { --sw-folder-color: var(--sw-fc-orange); }
.nav-folder:has(> .nav-folder-title[data-path="Archive"]) { --sw-folder-color: var(--sw-fc-grey); }
```

Available colors: `--sw-fc-mint`, `--sw-fc-lavender`, `--sw-fc-orange`, `--sw-fc-blue`, `--sw-fc-yellow`, `--sw-fc-forest`, `--sw-fc-grey`. Folders the snippet doesn't name keep their automatic color.

## Settings

Install the [Style Settings](https://github.com/mgmeyers/obsidian-style-settings) plugin to customize the theme:

- Font pairing for light mode and for dark mode:
  - A · Outfit × Newsreader (light default)
  - B · Manrope × Instrument Serif (dark default)
  - C · Plus Jakarta Sans × Young Serif
  - D · Hanken Grotesk × Gloock
  - E · Albert Sans × DM Mono
- Light mode variant: Cream or Forest
- Floating cards: dark mode only, always, or never
- Folder colors: automatic or off
- External link icon: ↗ arrow in the link color, none, or Obsidian's default
- H1 divider: show a thin line below level 1 headings (off by default)
- Drop cap in reading view
- Plain blockquotes and plain embeds

Without Style Settings, the theme uses the defaults listed above.

## Building from source

`theme.css` is generated. Edit `src/theme.css`, then run:

```bash
./build.sh
```

The script embeds the fonts from `fonts/` as base64, because Obsidian themes can't load font files stored next to them. To build and install into one or more vaults at once:

```bash
./build.sh ~/path/to/vault
```

## Releasing

Bump `version` in `manifest.json`, rebuild, commit, then push a tag with the same version (for example `1.0.1`). The release workflow attaches `manifest.json` and `theme.css` to a GitHub release.

## Changelog

### 1.0.3

- Make the H1 divider optional and disabled by default, with a toggle in Style Settings.
- Move all signifier rendering and configuration to the Suliworld Signifiers plugin. The theme now handles general appearance only.

### 1.0.2

- Renaming a file or folder in the file explorer shows a readable text field in every variant (the name was white on the field or on the yellow flash).
- With the Suliworld Signifiers companion plugin, every signifier is clickable (click to mark done, right-click or long-press for the menu). The README explains what the theme does alone and what the plugin adds.

### 1.0.1

- Highlights are rounded pills with padding around the text, in stronger colors (warm yellow in light mode, ochre in dark mode). In Live Preview, a highlight containing bold or italic text stays one pill.
- Folder colors in the file explorer: automatic by position, or set by folder name with a snippet. New Style Settings option to turn them off.

### 1.0.0

- First release.

## License

The theme is released under the [MIT License](LICENSE).

The bundled fonts are licensed under the SIL Open Font License 1.1. See [fonts/OFL.txt](fonts/OFL.txt) for their copyright notices: Outfit, Newsreader, Manrope, Instrument Serif, Plus Jakarta Sans, Young Serif, Hanken Grotesk, Gloock, Albert Sans, DM Mono, and iA Writer Duo.
