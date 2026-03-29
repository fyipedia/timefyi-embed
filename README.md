# timefyi-embed

[![npm](https://img.shields.io/npm/v/timefyi-embed)](https://www.npmjs.com/package/timefyi-embed)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/timefyi-embed)

Embed **TimeFYI** widgets — cities, glossary terms, interactive tools, and inline elements — on any website. **10 widget types**, zero dependencies, Shadow DOM style isolation, 4 built-in themes (light, dark, sepia, auto), 2 styles (modern, clean), and live data from the [TimeFYI](https://timefyi.com) database.

Every widget includes a "Powered by TimeFYI" backlink directing readers to the full reference.

> **Try the interactive widget builder at [widget.timefyi.com](https://widget.timefyi.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-timefyi="entity" data-slug="cities" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

That's it. The widget fetches data from the TimeFYI API and renders with full style isolation.

## Widget Types

| Type | Usage | Description |
|------|-------|-------------|
| `entity` | `<div data-timefyi="entity" data-slug="..."></div>` | Entity detail card — unit, city, holiday, or name |
| `glossary` | `<div data-timefyi="glossary" data-slug="..."></div>` | Glossary term definition with cross-references |
| `guide` | `<div data-timefyi="guide" data-slug="..."></div>` | Guide summary card with key takeaways |
| `search` | `<div data-timefyi="search" data-slug="..."></div>` | Search box linking to the full database |
| `compare` | `<div data-timefyi="compare" data-slug="..."></div>` | Side-by-side entity comparison |
| `faq` | `<div data-timefyi="faq" data-slug="..."></div>` | FAQ accordion with expand/collapse |
| `clock` | `<div data-timefyi="clock" data-slug="..."></div>` | Live world clock with 1-second updates |
| `sunrise` | `<div data-timefyi="sunrise" data-slug="..."></div>` | Sunrise/sunset times with visual day-length bar |
| `city-compare` | `<div data-timefyi="city-compare" data-slug="..."></div>` | Side-by-side two-city live time comparison |
| `timezone` | `<div data-timefyi="timezone" data-slug="..."></div>` | Inline timezone offset badge (e.g. "UTC+9") |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-timefyi` | entity, compare, glossary, guide, search, faq, [tools] | required | Widget type |
| `data-slug` | e.g. "cities" | — | Entity slug from the TimeFYI database |
| `data-theme` | light, dark, sepia, auto | light | Visual theme (`auto` follows OS preference) |
| `data-style` | modern, clean | modern | Widget design style |
| `data-size` | default, compact, large | default | Widget size |
| `data-placeholder` | any string | "Search Cities..." | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-timefyi="entity" data-slug="cities" data-theme="light"></div>

<!-- Dark -->
<div data-timefyi="entity" data-slug="cities" data-theme="dark"></div>

<!-- Sepia -->
<div data-timefyi="entity" data-slug="cities" data-theme="sepia"></div>

<!-- Auto — follows OS dark/light preference -->
<div data-timefyi="entity" data-slug="cities" data-theme="auto"></div>
```

## Styles

```html
<!-- Modern (default) — clean lines, rounded corners, accent gradients -->
<div data-timefyi="entity" data-slug="cities" data-style="modern"></div>

<!-- Clean — minimal borders, utility-focused, data-first aesthetic -->
<div data-timefyi="entity" data-slug="cities" data-style="clean"></div>
```

## Web Components (Custom Elements)

As an alternative to `data-*` attributes, you can use native HTML custom elements:

```html
<!-- Custom element form -->
<timefyi-entity slug="cities" theme="light"></timefyi-entity>
<timefyi-compare slugs="cities,other-slug"></timefyi-compare>
<timefyi-search placeholder="Search Cities..."></timefyi-search>

<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

Use `style-variant` (not `style`) to avoid conflicts with the HTML reserved `style` attribute.

## Examples

### Entity Card

```html
<div data-timefyi="entity" data-slug="cities" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

### Side-by-Side Comparison

```html
<div data-timefyi="compare" data-slugs="cities,other-slug"></div>
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-timefyi="search" data-placeholder="Search Cities..."></div>
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

### Glossary Term

```html
<div data-timefyi="glossary" data-slug="example-term" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
```

### Specific version (production stability)

```html
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1.0.0/dist/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install timefyi-embed
```

```javascript
import 'timefyi-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **2 styles**: Modern (accent gradients) and Clean (minimal, data-first)
- **4 themes**: Light, Dark, Sepia, Auto (OS preference detection)
- **CORS**: TimeFYI API has CORS enabled for all origins
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **IntersectionObserver**: Lazy loading — widgets only fetch when entering viewport (200px margin)
- **Rich Snippets**: DefinedTerm JSON-LD injected for glossary widgets
- **Bundle size**: Tree-shaken per site — only includes tools available on TimeFYI

## Learn More About Cities

Visit [timefyi.com](https://timefyi.com) — TimeFYI is a comprehensive cities reference with interactive tools, guides, and developer resources.

- **API docs**: [timefyi.com/developers/](https://timefyi.com/developers/)
- **Widget builder**: [widget.timefyi.com](https://widget.timefyi.com)
- **npm package**: [npmjs.com/package/timefyi-embed](https://www.npmjs.com/package/timefyi-embed)
- **GitHub**: [github.com/fyipedia/timefyi-embed](https://github.com/fyipedia/timefyi-embed)

## Utility FYI Family

Part of [FYIPedia](https://fyipedia.com) — open-source developer tools ecosystem. Utility FYI covers unit conversion, timezones, holidays, and names. Hub: [toolfyi.com](https://toolfyi.com).

| Site | Domain | Focus | Package |
|------|--------|-------|---------|
| UnitFYI | [unitfyi.com](https://unitfyi.com) | 220 units, 20 categories, offline converter | [npm](https://www.npmjs.com/package/unitfyi-embed) |
| **TimeFYI** | [timefyi.com](https://timefyi.com) | 6,040 cities, live world clock, sunrise data | **[npm](https://www.npmjs.com/package/timefyi-embed)** |
| HolidayFYI | [holidayfyi.com](https://holidayfyi.com) | 626 holidays, 197 countries, live today feed | [npm](https://www.npmjs.com/package/holidayfyi-embed) |
| NameFYI | [namefyi.com](https://namefyi.com) | 35,585 names, Hanja characters, Five Elements | [npm](https://www.npmjs.com/package/namefyi-embed) |

## FYIPedia Developer Tools

| Package | PyPI | npm | Description |
|---------|------|-----|-------------|
| colorfyi | [PyPI](https://pypi.org/project/colorfyi/) | [npm](https://www.npmjs.com/package/@fyipedia/colorfyi) | Color conversion, WCAG contrast, harmonies — [colorfyi.com](https://colorfyi.com) |
| emojifyi | [PyPI](https://pypi.org/project/emojifyi/) | [npm](https://www.npmjs.com/package/emojifyi) | Emoji encoding & metadata for 3,953 emojis — [emojifyi.com](https://emojifyi.com) |
| unitfyi | [PyPI](https://pypi.org/project/unitfyi/) | [npm](https://www.npmjs.com/package/unitfyi) | Unit conversion, 220 units — [unitfyi.com](https://unitfyi.com) |
| timefyi | [PyPI](https://pypi.org/project/timefyi/) | [npm](https://www.npmjs.com/package/timefyi) | Timezone ops & business hours — [timefyi.com](https://timefyi.com) |
| holidayfyi | [PyPI](https://pypi.org/project/holidayfyi/) | [npm](https://www.npmjs.com/package/holidayfyi) | Holiday dates & Easter calculation — [holidayfyi.com](https://holidayfyi.com) |
| namefyi | [PyPI](https://pypi.org/project/namefyi/) | [npm](https://www.npmjs.com/package/namefyi) | Korean romanization & Five Elements — [namefyi.com](https://namefyi.com) |
| fyipedia | [PyPI](https://pypi.org/project/fyipedia/) | — | Unified CLI for all FYI tools — [fyipedia.com](https://fyipedia.com) |

## Embed Widget

Embed [TimeFYI](https://timefyi.com) widgets on any website with [timefyi-embed](https://widget.timefyi.com):

```html
<script src="https://cdn.jsdelivr.net/npm/timefyi-embed@1/dist/embed.min.js"></script>
<div data-timefyi="entity" data-slug="example"></div>
```

Zero dependencies · Shadow DOM · 4 themes (light/dark/sepia/auto) · [Widget docs](https://widget.timefyi.com)

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [FYIPedia](https://fyipedia.com).
