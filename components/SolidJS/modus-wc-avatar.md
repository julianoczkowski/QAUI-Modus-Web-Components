---
tag: modus-wc-avatar
category: Data Display
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-avatar--docs
---

> [!info] **SolidJS Quick Start**
>
> 1. **Import** `@trimble-oss/modus-web-components/modus-wc-styles.css` once in your entry file.
> 2. **Set** `document.documentElement.dataset.theme = "modus-classic-light"` before hydration to avoid a flash of the wrong theme (FOWT).
> 3. **Bind** arrays/objects with **property bindings** (`prop:*`) or a helper such as `useOptions`; _never_ pass JSON strings via attributes.

# Modus WC Avatar

## Purpose

Shows a user or entity image in a circle or square, with four built‑in sizes and an accessible `alt` text requirement.

## Attributes

- **`alt`** - `string` **(required)** - Image alt attribute for screen‑reader users. _Reflected as prop_: **yes**
- **`img-src`** - `string` - Default: `''` - URL of the image file; if omitted the component may show a placeholder in future releases. _Reflected as prop_: **yes**
- **`shape`** - `"circle" | "square"` - Default: `circle` - Circle is typical for profile pictures; square matches data‑tables or cards. _Reflected as prop_: **yes**
- **`size`** - `"xs" | "sm" | "md" | "lg"` - Default: `md` - Token drives width/height (e.g. xs = 24 px, sm = 32 px, md = 40 px, lg = 64 px). _Reflected as prop_: **yes**
- **`custom-class`** - `string` - Default: `''` - Adds extra class(es) to the inner wrapper for bespoke borders, shadows, etc. _Reflected as prop_: **yes**

## Events

_None_

## Usage

### HTML Example

```html
<!-- Default circle, medium -->
<modus-wc-avatar
  alt="Ada Lovelace"
  img-src="https://example.com/avatars/ada.jpg"
>
</modus-wc-avatar>

<!-- Square, small -->
<modus-wc-avatar
  alt="Square avatar"
  img-src="https://example.com/avatars/square.png"
  shape="square"
  size="sm"
>
</modus-wc-avatar>

<!-- Large circle with custom border -->
<style>
  .ring {
    box-shadow: 0 0 0 3px var(--modus-primary, #0076ff);
    border-radius: 50%;
  }
</style>
<modus-wc-avatar
  alt="Avatar with ring"
  img-src="https://example.com/avatars/ring.jpg"
  size="lg"
  custom-class="ring"
>
</modus-wc-avatar>
```

### SolidJS Example

```tsx
// entry.tsx
import "@trimble-oss/modus-web-components/modus-wc-styles.css";
document.documentElement.dataset.theme = "modus-classic-light";

// AvatarExample.tsx
import { createSignal } from "solid-js";

export function AvatarExample() {
  const [size, setSize] = createSignal<"xs" | "sm" | "md" | "lg">("md");
  const [shape, setShape] = createSignal<"circle" | "square">("circle");

  // Example user data
  const user = {
    name: "Ada Lovelace",
    imageUrl:
      "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg",
  };

  return (
    <div>
      <h3>Avatar Component</h3>

      <div style="display: flex; gap: 1rem; align-items: center; margin-bottom: 1rem;">
        <modus-wc-avatar
          alt={user.name}
          img-src={user.imageUrl}
          prop:size={size()}
          prop:shape={shape()}
        />

        <div>
          <p>
            <strong>{user.name}</strong>
          </p>
          <p>First computer programmer</p>
        </div>
      </div>

      <div style="display: flex; gap: 1rem; margin-bottom: 1rem;">
        <span>Size:</span>
        {["xs", "sm", "md", "lg"].map((s) => (
          <modus-wc-button
            color={size() === s ? "primary" : "secondary"}
            variant="outlined"
            size="sm"
            on:click={() => setSize(s as any)}
          >
            {s}
          </modus-wc-button>
        ))}
      </div>

      <div style="display: flex; gap: 1rem;">
        <span>Shape:</span>
        {["circle", "square"].map((s) => (
          <modus-wc-button
            color={shape() === s ? "primary" : "secondary"}
            variant="outlined"
            size="sm"
            on:click={() => setShape(s as any)}
          >
            {s}
          </modus-wc-button>
        ))}
      </div>
    </div>
  );
}
```

> [!tip] **SolidJS Note**
> String enums (`size`, `shape`) should be passed with `prop:` directives when they come from signals, e.g. `prop:size={size()}`.

### Pattern notes

- **Accessibility:** `alt` is mandatory; keep it meaningful (e.g. user's full name).
- **Fallback images:** if `img-src` is empty or fails to load, the component may show initials or a generic icon in future versions—plan for this.
- **Sizing:** avatar sizes map to the same tokens used in other Modus inputs, so grids stay aligned.
- **Custom styling:** prefer `custom-class` over deep selectors to avoid breaking internals.

---

## Helper: `useOptions`

For components that accept complex options objects, use this helper:

```ts
import { onMount, createEffect } from "solid-js";

export function useOptions<T>(
  el: () => HTMLElement | undefined,
  options: () => T
) {
  onMount(() => (el()?.options = options()));
  createEffect(() => (el()?.options = options()));
}
```

---

## Theming & Icons

- Reference colours/spacing with CSS variables such as `--modus-primary`; never hard-code values.
- Choose **one** icon strategy—font, SVG sprite, or `<modus-icon>`—to keep bundles lean; mixing is discouraged.
