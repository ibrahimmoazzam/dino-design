# @dino-labs/tokens

Design tokens for [Fossil Design](https://github.com/ibrahimmoazzam/dino-design), an open-source agentic design system: CSS custom properties for light and dark mode, metadata for tools and agents, and typed keys for component props.

> **Early release.** Versions `0.x` may rename tokens between minor versions while the taxonomy settles. Renames keep a deprecated alias first, and the release notes list each one.

## Install

```sh
npm install @dino-labs/tokens
```

## Use the custom properties

Import the stylesheet once, then style with the semantic tokens:

```js
import '@dino-labs/tokens/tokens.css';
```

```css
.card {
  padding: var(--dino-space-m);
  border-radius: var(--dino-radius-surface);
  background: var(--dino-color-background-surface);
  color: var(--dino-color-text-default);
}
```

- **Semantic tokens only.** Primitive tokens such as `--dino-base-color-gray-600` hold the raw values that semantic tokens alias. Style with the semantic ones, so a change to a primitive restyles everything built on it.
- **Dark mode is built in.** It follows the system's setting. Set `data-theme="light"` or `data-theme="dark"` on `<html>` to choose one.
- **A text style is five properties.** Set all five; the `font` shorthand drops letter-spacing.

  ```css
  .title {
    font-family: var(--dino-text-heading-s-font-family);
    font-size: var(--dino-text-heading-s-font-size);
    font-weight: var(--dino-text-heading-s-font-weight);
    letter-spacing: var(--dino-text-heading-s-letter-spacing);
    line-height: var(--dino-text-heading-s-line-height);
  }
  ```

- **No fonts are included.** The font tokens name Space Grotesk, Space Mono and Figtree, which are on Google Fonts. Load them in your app, or point `--dino-font-family-heading`, `-body` and `-mono` at your own faces.

## Use the tokens in TypeScript

```ts
import { mediaQueries, tokenKeys, type TokenKey } from '@dino-labs/tokens';

type Gap = TokenKey<'space'>; // '2xs' | 'xs' | 's' | 'm' | 'l' | 'xl' | '2xl' | '3xl'

const isTablet = window.matchMedia(mediaQueries.tablet).matches;
```

Custom properties can't be used in media queries, so the breakpoints are also exported as values and media query strings.

The JSON files come typed: `import tokens from '@dino-labs/tokens/tokens.json' with { type: 'json' }` is a `TokensFile`.

## What's inside

| Import                          | Contents                                                                                                                          |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `@dino-labs/tokens/tokens.css`  | Every token as a custom property, with dark values                                                                                |
| `@dino-labs/tokens/tokens.json` | Each token's custom property, resolved value, alias, dark value, description and deprecation, keyed by path                       |
| `@dino-labs/tokens/lint.json`   | The primitive and deprecated custom properties, for `@dino-labs/stylelint-config`                                                 |
| `@dino-labs/tokens`             | `tokenKeys`, `breakpoints` and `mediaQueries`, and the types `TokenKey`, `TokenGroup`, `Breakpoint`, `TokensFile` and `LintLists` |

The token source is DTCG 2025.10 JSON in the [repository](https://github.com/ibrahimmoazzam/dino-design/tree/main/packages/tokens/src), built with Style Dictionary.

## License

MIT © 2026 Ibrahim Moazzam. See [LICENSE](./LICENSE).
