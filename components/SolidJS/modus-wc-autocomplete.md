---
tag: modus-wc-autocomplete
category: Forms & Data Entry
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-forms-autocomplete--docs
---

> [!info] **SolidJS Quick Start**
>
> 1. **Import** `@trimble-oss/modus-web-components/modus-wc-styles.css` once in your entry file.
> 2. **Set** `document.documentElement.dataset.theme = "modus-classic-light"` before hydration to avoid a flash of the wrong theme (FOWT).
> 3. **Bind** arrays/objects with **property bindings** (`prop:*`) or a helper such as `useOptions`; _never_ pass JSON strings via attributes.

# Modus WC Autocomplete

## Purpose

Provides a text‑input that suggests results as you type. Supports single or multiple selection, debounced search, custom "no results" content, and fully slotted menu items.

## Attributes

- **`bordered`** - `boolean` - Default: `true` - Adds a border around the control. _Reflected as prop_: **yes**
- **`disabled`** - `boolean` - Default: `false` - Disables keyboard & pointer interaction. _Reflected as prop_: **yes**
- **`multi-select`** - `boolean` - Default: `false` - Allows multiple chips to be selected. _Reflected as prop_: **yes**
- **`items`** - `IAutocompleteItem[]` - Default: `[]` - Array of objects shown in the dropdown; create a **new array** on every update to trigger re‑render. _Reflected as prop_: **yes**
- **`value`** - `string` - Default: `''` - Current text value / chip search string. _Reflected as prop_: **yes**
- **`placeholder`** - `string` - Default: `''` - Grey helper text when no value present. _Reflected as prop_: **yes**
- **`label`** - `string` - Default: `undefined` - Floating label text above the field. _Reflected as prop_: **yes**
- **`size`** - `"sm" | "md" | "lg"` - Default: `md` - Adjusts height & typography. _Reflected as prop_: **yes**
- **`debounce-ms`** - `number` - Default: `300` - Delay before `inputChange` fires; set to `0` to disable. _Reflected as prop_: **yes**
- **`min-chars`** - `number` - Default: `0` - Minimum characters before the menu shows. _Reflected as prop_: **yes**
- **`leave-menu-open`** - `boolean` - Default: `false` - Keeps dropdown open after selection (good for multi‑select). _Reflected as prop_: **yes**
- **`show-spinner`** - `boolean` - Default: `false` - Shows loading spinner while fetching remote data. _Reflected as prop_: **yes**
- **`no-results`** - `IAutocompleteNoResults` - Default: see interface - Object that customises the "no results" panel. _Reflected as prop_: **yes**

_(Additional props `custom-class`, `read-only`, `required`, `input-id`, `input-tab-index`, `name` are also available.)_

## Events

- **`inputChange`** - `CustomEvent<Event>` - Debounced every `debounce-ms`.
- **`inputFocus`** / **`inputBlur`** - `CustomEvent<FocusEvent>` - Focus gained / lost.
- **`itemSelect`** - `CustomEvent<IAutocompleteItem>` - Item picked.
- **`chipRemove`** - `CustomEvent<IAutocompleteItem>` - Chip removed in multi‑select.

## Usage

### HTML Example

```html
<!-- Single‑select, default spinner off -->
<modus-wc-autocomplete
  aria-label="Fruit autocomplete"
  label="Select a Fruit"
  placeholder="Type to search..."
  .items=${[
    { label: 'Apple',  value: 'apple',  visibleInMenu: true },
    { label: 'Banana', value: 'banana', visibleInMenu: true },
    { label: 'Pear',   value: 'pear',   visibleInMenu: true }
  ]}
  @inputChange=${e => {
    const ac = e.target;
    const txt = e.detail.target.value.toLowerCase();
    ac.items = ac.items.map(it => ({ ...it, visibleInMenu: it.label.toLowerCase().includes(txt) }));
  }}
  @itemSelect=${e => console.log('Selected', e.detail)}>
</modus-wc-autocomplete>

<!-- Multi‑select with chips -->
<modus-wc-autocomplete
  multi-select
  label="Select fruits"
  placeholder="Start typing..."
  leave-menu-open
  .items=${[
    { label: 'Apple', value: 'apple', visibleInMenu: true },
    { label: 'Orange', value: 'orange', visibleInMenu: true }
  ]}
  @chipRemove=${e => console.log('Removed', e.detail)}>
</modus-wc-autocomplete>

<!-- Remote search with spinner -->
<modus-wc-autocomplete id="remote-ac" label="Search users" show-spinner></modus-wc-autocomplete>
<script type="module">
  const ac = document.getElementById('remote-ac');
  ac.addEventListener('inputChange', async e => {
    const q = e.detail.target.value;
    if (!q) return;
    ac.showSpinner = true;
    const res = await fetch(`/api/users?q=${encodeURIComponent(q)}`).then(r => r.json());
    ac.items = res.map(u => ({ label: u.name, value: u.id, visibleInMenu: true }));
    ac.showSpinner = false;
  });
</script>
```

### SolidJS Example

```tsx
// entry.tsx
import "@trimble-oss/modus-web-components/modus-wc-styles.css";
document.documentElement.dataset.theme = "modus-classic-light";

// AutocompleteExample.tsx
import { createSignal, createEffect } from "solid-js";

export function AutocompleteExample() {
  const [items, setItems] = createSignal([
    { label: "Apple", value: "apple", visibleInMenu: true },
    { label: "Banana", value: "banana", visibleInMenu: true },
    { label: "Orange", value: "orange", visibleInMenu: true },
    { label: "Pear", value: "pear", visibleInMenu: true },
    { label: "Strawberry", value: "strawberry", visibleInMenu: true },
  ]);

  const [loading, setLoading] = createSignal(false);
  const [selectedItems, setSelectedItems] = createSignal<any[]>([]);
  let autocompleteRef!: HTMLModusWcAutocompleteElement;

  const handleInputChange = (e: CustomEvent) => {
    const searchText = e.detail.target.value.toLowerCase();

    // Simulate API delay
    setLoading(true);
    setTimeout(() => {
      setItems((prev) =>
        prev.map((item) => ({
          ...item,
          visibleInMenu: item.label.toLowerCase().includes(searchText),
        }))
      );
      setLoading(false);
    }, 300);
  };

  const handleItemSelect = (e: CustomEvent) => {
    const selected = e.detail;
    setSelectedItems((prev) => [...prev, selected]);
  };

  const handleChipRemove = (e: CustomEvent) => {
    const removed = e.detail;
    setSelectedItems((prev) =>
      prev.filter((item) => item.value !== removed.value)
    );
  };

  return (
    <div>
      <h3>SolidJS Autocomplete Example</h3>

      <modus-wc-autocomplete
        ref={autocompleteRef}
        label="Select Fruits"
        placeholder="Type to search..."
        prop:multi-select={true}
        prop:leave-menu-open={true}
        prop:show-spinner={loading()}
        prop:items={items()}
        on:inputChange={handleInputChange}
        on:itemSelect={handleItemSelect}
        on:chipRemove={handleChipRemove}
      />

      <div style="margin-top: 1rem">
        <h4>Selected Items:</h4>
        <ul>
          {selectedItems().map((item) => (
            <li>{item.label}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}
```

> [!tip] **SolidJS Note**
> Boolean flags (`multi-select`, `leave-menu-open`, etc.) and all array/object props must be set with `prop:` directives, e.g. `prop:items={items()}`.

### Slot support

- **`menu-items`** — supply fully custom `<li>` elements; you handle filtering and emit `itemSelect` manually when an item is chosen.

### Pattern notes

- **Controlled input:** always assign a _new_ `items` array after filtering to trigger re‑render.
- **Debounce:** lower `debounce-ms` for live‑search; set to `0` for instant updates.
- **Multi‑select chips:** read `items[].selected` to display chips; listen for `chipRemove` to update state.
- **Accessibility:** keyboard navigation handled internally; set `aria-label` for screen‑reader context.

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
