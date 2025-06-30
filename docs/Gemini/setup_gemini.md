# Modus Web Components — Setup

A minimal one-time boiler-plate that every HTML page using Modus Web Components needs.

---

## 1. CSS

```html
<!-- Modus component tokens & styles -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/moduswebcomponents/modus-wc-styles.css"
/>

<!-- Tailwind CSS for utility classes -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Modus Icons -->
<link
  rel="preload"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/field-systems/fonts/modus-icons.css"
  as="style"
  crossorigin="anonymous"
/>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/field-systems/fonts/modus-icons.css"
/>

<!-- Google Fonts: Open Sans -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap"
  rel="stylesheet"
/>

<!-- Chart.js for data visualization -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
```

## 3. Theme attribute

The root `<html>` tag must carry a `data-theme` that matches one of the shipped themes. modus-classic-light is the default one.

```html
<html lang="en" data-theme="modus-classic-light"></html>
```

Available values: `modus-classic-light` · `modus-classic-dark`.

---

## 4. Runtime theme switch helper

```html
<select
  onchange="document.documentElement.setAttribute('data-theme', this.value)"
>
  <option value="modus-classic-light">Classic Light</option>
  <option value="modus-classic-dark">Classic Dark</option>
</select>
```

Persist the user's choice by writing the value to `localStorage` and re-applying it on `DOMContentLoaded` if desired.

---
