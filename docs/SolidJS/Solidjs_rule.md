Below is a single, streamlined **Solid JS integration rule** for using **Modus 2 Web Components (Classic theme)**.

---

### Key take-aways (one-paragraph summary)

Install the framework-agnostic package **`@trimble-oss/modus-web-components`** and its global style sheet once, set the `data-theme` attribute before hydration, and author components with Solid’s fine-grained primitives (`createSignal`, `createEffect`, `createResource`). Use direct refs to call imperative APIs and a tiny `useOptions` helper when a Modus element exposes an `options` property. Wrap data fetches in `<Suspense>` and pages in `<ErrorBoundary>`, pick exactly one icon-loading strategy, and lean on CSS custom properties (`--modus-primary`, etc.) for theming. Follow the kebab-case folder pattern and named exports, and keep signals primitive for best performance.

---

## 1. Installation & Bootstrap

| Step              | Command / Code                                                          | Why                                       |
| ----------------- | ----------------------------------------------------------------------- | ----------------------------------------- |
| **Install once**  | `npm i @trimble-oss/modus-web-components@<locked-version>`              | Core package with built-in type defs      |
| **Global CSS**    | `ts\nimport "@trimble-oss/modus-web-components/modus-wc-styles.css";\n` | Shadow-DOM parts resolve tokens correctly |
| **Theme upfront** | `ts\ndocument.documentElement.dataset.theme = "modus-classic-light";\n` | Prevent flash of wrong theme (FOWT)       |

---

## 2. Authoring Modus Elements in Solid

| Goal                        | Guideline                                                                                      |
| --------------------------- | ---------------------------------------------------------------------------------------------- |
| **State**                   | Use `createSignal` for local values                                                            |
| **Async data**              | Fetch with `createResource` and wrap UI in `<Suspense>`                                        |
| **Side-effects**            | Keep DOM tweaks inside `createEffect`                                                          |
| **Refs / Imperative API**   | `ref={el => accordionEl = el}` then call methods in `onMount`; Solid refs are live after mount |
| **Complex `options` props** | Update once in `onMount` **and** reactively via `createEffect`; see `useOptions` helper below  |
| **Typed custom events**     | Handle with `on:eventName` & `CustomEvent<Payload>` payloads for full IntelliSense             |

---

## 3. Async Loading & Error Handling

- `<Suspense fallback={<Spinner/>}>` around any component that waits on a resource
- `<ErrorBoundary fallback={ErrorView}/>` at route level to catch unexpected throws

---

## 4. Theming & Icons

- **Tokens** – consume CSS vars like `--modus-primary`; never hard-code colours
- **Choose one icon path**:

  1. Font CDN (`@trimble-oss/modus-icons`),
  2. SVG sprite, or
  3. upcoming `<modus-icon>` element.
     Mixing strategies inflates bundles; SVG gives best fidelity

---

## 5. Directory & Naming Pattern

```
src/
 ├─ components/
 │   └─ user-card/
 │       ├─ user-card.tsx   # named export
 │       ├─ helpers.ts
 │       └─ content.ts
 ├─ routes/
 └─ services/
```

- Folders **kebab-case**; files with JSX end **`.tsx`**.
- **Named exports only** keep tree-shaking clean

---

## 6. `useOptions` Helper

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

Bridges reactive signals to imperative `options` APIs (e.g., `modus-wc-accordion`).

---

## 7. Performance Checklist

- Store **primitive** values in signals to maximise fine-grained reactivity
- Lazy-load heavy widgets:

  ```ts
  const BigChart = lazy(() => import("./BigChart"));
  ```

  Solid auto-adds a Suspense boundary

---

### What you get by following these rules

- **WCAG-AA** colour contrast out-of-the-box.
- Micro-fast UI thanks to Solid’s signal system and zero wrapper overhead.
- Uniform theming and icon pipeline aligned with Trimble’s Modus Classic design.
- Predictable file structure and type-safe event handling for long-term maintainability.
