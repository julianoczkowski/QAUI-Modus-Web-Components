#

---

## How It Works

Instead of a pre-defined class like `bg-blue-600`, you use square brackets `[]` to pass the exact CSS value you want. Since the Modus stylesheet has already defined the color variables, you can use the `var()` function inside the brackets.

- **Instead of:** `bg-primary` (which requires config)
- **You will use:** `bg-[var(--modus-wc-color-primary)]`

## This approach combines the power of the Modus theming system with the convenience of Tailwind's utility classes.

### A Practical Guide to Styling Buttons with Modus Variables and Tailwind

Here is a guide that mirrors the `modus-wc-button` documentation, but uses Tailwind's arbitrary value syntax to pull colors from the linked Modus stylesheet.

**Important:** For the theme-based colors (like `--modus-wc-color-primary`) to work, you must set the theme class on a parent element, typically `<html>` or `<body>`.

```html
<!-- Add the desired theme class to a parent element -->
<html class="modus-modern-light">
  <body>
    <!-- Your buttons go here -->
  </body>
</html>
```

#### 1. Base Styles

Apply these classes to every button. They use standard Tailwind utilities.

```html
<button
  class="
  <!-- Layout & Font -->
  inline-flex items-center justify-center font-semibold

  <!-- Transitions -->
  transition-all

  <!-- Focus States (using a Modus variable for the ring) -->
  focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[var(--modus-wc-color-highlight-blue)]

  <!-- Disabled State -->
  disabled:opacity-50 disabled:cursor-not-allowed
"
>
  <!-- Content -->
</button>
```

#### 2. Size (`size`)

These are standard Tailwind classes and do not require variables.

| Modus Size         | Tailwind CSS Classes             |
| :----------------- | :------------------------------- |
| `xs`               | `px-2.5 py-1.5 text-xs rounded`  |
| `sm`               | `px-3 py-2 text-sm rounded-md`   |
| `md` **(Default)** | `px-4 py-2 text-base rounded-md` |
| `lg`               | `px-6 py-3 text-base rounded-lg` |

#### 3. Shape (`shape`)

Use these for icon-only buttons.

| Modus Shape | Tailwind CSS Class                  |
| :---------- | :---------------------------------- |
| `rectangle` | `rounded-md` (already part of size) |
| `square`    | `rounded-md` (already part of size) |
| `circle`    | `rounded-full`                      |

#### 4. Variant & Color (`variant` & `color`)

This is where you will use the Modus CSS variables. The classes below are designed to work with themes like `modus-modern-light` and `modus-modern-dark` by using semantic variable names.

| Attribute           | Modus Variable                     | Tailwind Arbitrary Class                       |
| :------------------ | :--------------------------------- | :--------------------------------------------- |
| **Primary**         | `--modus-wc-color-primary`         | `bg-[var(--modus-wc-color-primary)]`           |
| **Primary Content** | `--modus-wc-color-primary-content` | `text-[var(--modus-wc-color-primary-content)]` |
| **Secondary/Base**  | `--modus-wc-color-base-300`        | `bg-[var(--modus-wc-color-base-300)]`          |
| **Text/Content**    | `--modus-wc-color-base-content`    | `text-[var(--modus-wc-color-base-content)]`    |
| **Danger**          | `--modus-wc-color-red`             | `bg-[var(--modus-wc-color-red)]`               |
| **Warning**         | `--modus-wc-color-yellow`          | `bg-[var(--modus-wc-color-yellow)]`            |
| **Success**         | `--modus-wc-color-green`           | `bg-[var(--modus-wc-color-green)]`             |
| **Info**            | `--modus-wc-color-info`            | `bg-[var(--modus-wc-color-info)]`              |

---

### Complete Examples

#### Example 1: `Filled Primary` Button

This button will automatically adapt to the `modus-modern-light` or `modus-modern-dark` theme set on the `<html>` tag.

```html
<!--
  Corresponds to:
  <modus-wc-button color="primary" variant="filled">Save</modus-wc-button>
-->
<button
  type="button"
  class="
    inline-flex items-center justify-center font-semibold transition-all
    focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[var(--modus-wc-color-highlight-blue)]
    disabled:opacity-50 disabled:cursor-not-allowed
    px-4 py-2 text-base rounded-md

    <!-- Variant & Color -->
    bg-[var(--modus-wc-color-primary)]
    text-[var(--modus-wc-color-primary-content)]
    hover:brightness-90
  "
>
  Save
</button>
```

#### Example 2: `Outlined Danger` Button

```html
<!--
  Corresponds to:
  <modus-wc-button color="danger" variant="outlined">Delete</modus-wc-button>
-->
<button
  type="button"
  class="
    inline-flex items-center justify-center font-semibold transition-all
    focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[var(--modus-wc-color-highlight-blue)]
    disabled:opacity-50 disabled:cursor-not-allowed
    px-4 py-2 text-base rounded-md

    <!-- Variant & Color -->
    border border-[var(--modus-wc-color-red)]
    text-[var(--modus-wc-color-red)]
    bg-transparent
    hover:bg-[var(--modus-wc-color-red)]
    hover:text-[var(--modus-wc-color-white)]
  "
>
  Delete
</button>
```

#### Example 3: `Borderless Secondary` Button (Icon-only Circle)

This uses the base content colors for a subtle look.

```html
<!--
  Corresponds to:
  <modus-wc-button color="secondary" variant="borderless" shape="circle">
    <icon/>
  </modus-wc-button>
-->
<button
  aria-label="More options"
  type="button"
  class="
    inline-flex items-center justify-center font-semibold transition-all
    focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[var(--modus-wc-color-highlight-blue)]
    disabled:opacity-50 disabled:cursor-not-allowed
    p-2 text-base rounded-full

    <!-- Variant & Color -->
    text-[var(--modus-wc-color-base-content)]
    bg-transparent
    hover:bg-[var(--modus-wc-color-base-200)]
  "
>
  <!-- SVG Icon goes here -->
  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">...</svg>
</button>
```

This method gives you the full power of the Modus design system's colors and theming while allowing you to write semantic HTML styled with flexible Tailwind utilities, all without touching a config file.
