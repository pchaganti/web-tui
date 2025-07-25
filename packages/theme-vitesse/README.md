# @webtui/theme-vitesse

A port of the [Vitesse](https://github.com/antfu/vscode-theme-vitesse) color palette to [WebTUI](https://github.com/webtui/webtui).

Provides additional variants for the listed components in the base WebTUI library and supports both dark (default) and light themes with multiple contrast levels.

## Installation

Install the theme with your preferred package manager

```bash
bun i @webtui/theme-vitesse
npm i @webtui/theme-vitesse
yarn add @webtui/theme-vitesse
pnpm i @webtui/theme-vitesse
```

Ensure you import the theme **after** all the other stylesheets from `@webtui/css` or the styles will not be applied.

```css
@layer base, utils, components;

@import "@webtui/css/base.css";
@import "@webtui/css/components/typography.css";
/* ... */

@import "@webtui/theme-vitesse";
```

Set the `data-webtui-theme` attribute on the `<html>` tag or a container element.

```html
<html data-webtui-theme="vitesse-dark"></html>
```

To only apply the theme to a specific element:

```html
<html data-webtui-theme="dark">
  <!-- Example base theme -->
  <body>
    <div data-webtui-theme="vitesse-light-soft">
      <!-- Vitesse light-soft styles applied here -->
    </div>
    <div data-webtui-theme="vitesse-dark-soft">
      <!-- Vitesse dark-soft styles applied here -->
    </div>
  </body>
</html>
```

## Variants

Supports dark and light modes, each with hard, medium, and soft contrast levels.

```html
<!-- Dark Variants -->
<html data-webtui-theme="vitesse-black">
<html data-webtui-theme="vitesse-dark-soft">
<!-- Default: vitesse-dark or vitesse-black -->
<html data-webtui-theme="vitesse-dark">
<!-- Light Variants -->
<html data-webtui-theme="vitesse-light">
<!-- Default: vitesse-light -->
<html data-webtui-theme="vitesse-light-soft">
```

## Components

Components affected/modified by the theme:

- [Typography](#typography)
- [Badge](#badge)
- [Button](#button)

### Typography

- Colors headings from `h1` to `h6` using `var(--green)`.
- Inline `<a>` tags are underlined and colored `var(--blue)`, changing to `var(--aqua)` on hover.
- Inline `<code>` tags are colored `var(--orange)`.

```html
<h1>Heading 1</h1>
<!-- ... -->
<h6>Heading 6</h6>

<p><a href="https://example.com">Link</a> <code>Inline Code</code></p>
```

### Badge

Adds additional variants to badges matching Vitesse accent colors.

```html
<span is-="badge" variant-="gray">gray</span>
<span is-="badge" variant-="red">red</span>
<!-- ... -->
<span is-="badge" variant-="aqua">aqua</span>
<span is-="badge" variant-="orange">orange</span>
```

### Button

Adds additional variants to buttons matching Vitesse accent colors.

```html
<button variant-="gray">gray</button>
<button variant-="red">red</button>
<!-- ... -->
<button variant-="aqua">aqua</button>
<button variant-="orange">orange</button>
```

## CSS Variables

Adds the following CSS variables within the `base` layer, each of which change based on the theme variant

```css
[data-webtui-theme="vitesse-*-*"] {
  --bg1: #2f363d;
  --bg2: #393a34;
  --bg3: #444d56;
  --bg4: #586069;
  --fg0: #dbd7ca;
  --fg1: #c9c8c0;
  --fg2: #b8bab7;
  --fg3: #a6abae;
  --fg4: #959da5;

  --gray: #586069;
  --red: #cb7676;
  --green: #4d9375;
  --yellow: #e6cc77;
  --blue: #6394bf;
  --purple: #d9739f;
  --aqua: #5eaab5;
  --orange: #d4976c;
}
```

The base background/foreground colors use the following CSS variables from the Vitesse palette

```css
[data-webtui-theme="vitesse-*-*"] {
  --background0: var(--bg0);
  --background1: var(--bg1);
  --background2: var(--bg2);
  --background3: var(--bg3);

  --foreground0: var(--fg0);
  --foreground1: var(--fg1);
  --foreground2: var(--fg2);
}
```
