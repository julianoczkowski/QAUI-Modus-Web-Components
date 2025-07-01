---
tag: modus-wc-accordion
category: Navigation & Disclosure
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-accordion--docs
---

> [!info] **SolidJS Quick Start**
>
> 1. **Import** `@trimble-oss/modus-web-components/modus-wc-styles.css` once in your entry file.
> 2. **Set** `document.documentElement.dataset.theme = "modus-classic-light"` before hydration to avoid a flash of the wrong theme (FOWT).
> 3. **Bind** arrays/objects with **property bindings** (`prop:*`) or a helper such as `useOptions`; _never_ pass JSON strings via attributes.

# Modus WC Accordion

## Purpose

`modus-wc-accordion` is a lightweight container that groups one or more `modus-wc-collapse` items and coordinates their expand/collapse state.

## Attributes

| Name           | Type     | Default | Notes                                                                                       | Reflected |
| -------------- | -------- | ------- | ------------------------------------------------------------------------------------------- | --------- |
| `custom-class` | `string` | `''`    | Adds an extra CSS class to the accordion's inner wrapper so you can tweak layout or spacing | ✅        |

_All other behaviour is controlled by the child `modus-wc-collapse` components placed in the default slot._

## Events

| Event            | Payload                                             | Description                                                                    |
| ---------------- | --------------------------------------------------- | ------------------------------------------------------------------------------ |
| `expandedChange` | `CustomEvent<{ expanded: boolean; index: number }>` | Fires when a child collapse toggles. Handle in Solid with `on:expandedChange`. |

## ⚠️ Collapse Configuration

> [!warning] **Important** > `modus-wc-collapse` **does not** accept a `title` attribute. Configure titles (and other metadata) through the **`options` property**:

```html
<!-- ❌ WRONG -->
<modus-wc-collapse collapse-id="item1" title="Won't work"></modus-wc-collapse>

<!-- ✅ RIGHT -->
<modus-wc-collapse id="collapse1" collapse-id="item1"></modus-wc-collapse>
<script type="module">
  collapse1.options = {
    title: "Works!",
    description: "Optional subtitle",
    icon: "help", // valid Modus icon name
  };
</script>
```

## Usage

### HTML Example

```html
<modus-wc-accordion>
  <modus-wc-collapse id="collapse1" collapse-id="item1">
    <div slot="content">Content for item one.</div>
  </modus-wc-collapse>
  <modus-wc-collapse id="collapse2" collapse-id="item2">
    <div slot="content">Content for item two.</div>
  </modus-wc-collapse>
  <modus-wc-collapse id="collapse3" collapse-id="item3">
    <div slot="content">Content for item three.</div>
  </modus-wc-collapse>
</modus-wc-accordion>

<script type="module">
  // Configure collapse options
  collapse1.options = { title: "Item One", icon: "star" };
  collapse2.options = { title: "Item Two", icon: "settings" };
  collapse3.options = { title: "Item Three", icon: "help" };

  // Listen for accordion events
  document
    .querySelector("modus-wc-accordion")
    .addEventListener("expandedChange", (e) => {
      console.log(
        `Item ${e.detail.index} is ${e.detail.expanded ? "open" : "closed"}`
      );
    });
</script>
```

### SolidJS Example

```tsx
// entry.tsx
import "@trimble-oss/modus-web-components/modus-wc-styles.css";
document.documentElement.dataset.theme = "modus-classic-light";

// AccordionExample.tsx
import { onMount } from "solid-js";

export function AccordionExample() {
  let acc!: HTMLModusWcAccordionElement;

  onMount(() => {
    const [c1, c2] =
      acc.querySelectorAll<HTMLModusWcCollapseElement>("modus-wc-collapse");
    c1.options = { title: "Item One", icon: "star" };
    c2.options = { title: "Item Two", icon: "settings" };
  });

  return (
    <modus-wc-accordion
      ref={acc}
      on:expandedChange={(e) => {
        const { index, expanded } = (
          e as CustomEvent<{ index: number; expanded: boolean }>
        ).detail;
        console.log(index, expanded);
      }}
    >
      <modus-wc-collapse collapse-id="item1">
        <div slot="content">Content 1</div>
      </modus-wc-collapse>
      <modus-wc-collapse collapse-id="item2">
        <div slot="content">Content 2</div>
      </modus-wc-collapse>
    </modus-wc-accordion>
  );
}
```

> [!tip] **SolidJS Note**
> Boolean flags (`disabled`, `open`, etc.) and all array/object props must be set with `prop:` directives, e.g. `prop:disabled={isOpen()}`.

---

## Helper: `useOptions`

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

Use this helper whenever an `options` object needs to stay in sync with reactive state.

---

## Theming & Icons

- Reference colours/spacing with CSS variables such as `--modus-primary`; never hard-code values.
- Choose **one** icon strategy—font, SVG sprite, or `<modus-icon>`—to keep bundles lean; mixing is discouraged.

```

```
