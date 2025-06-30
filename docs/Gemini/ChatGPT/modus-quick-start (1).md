---
title: "Modus Quick‑Start"
version: "1.0.0"
theme-default: "modus-classic-light"
---

## Step 1: Add links {{#add-links}}

> 💡 Loads Modus Classic styles, icon font, Google Fonts, Tailwind, and Chart.js  
> (All URLs are unchanged from your original markdown.)

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-web-components@latest/dist/modus-wc-styles.css"
/>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap"
  rel="stylesheet"
/>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/field-systems/fonts/modus-icons.css"
/>
<script src="https://cdn.tailwindcss.com"></script>
```

## Step 2: Set the default theme {{#set-default-theme}}

```html
<html lang="en" data-theme="modus-classic-light">
  <!-- Your content here -->
</html>
```

## Step 3: Use Modus Icons {{#use-icons}}

> 💡 _Modus icons are delivered as a font._  
> Add an `<i>` tag with the class `modus-icons`; put the icon’s name as text between the tags.

##### **Basic Usage**

```html
<!-- Renders a lightbulb icon -->
<i class="modus-icons">lightbulb_on</i>

<!-- Renders a settings icon -->
<i class="modus-icons">settings</i>
```

##### **Customizing Size and Color**

Because they’re font icons, you can change their look with standard `font-size` and `color` CSS:

```html
<!-- A larger, orange lightbulb icon -->
<i class="modus-icons" style="font-size: 2rem; color: orange;">lightbulb_on</i>

<!-- A button with a customized icon -->
<button class="modus-wc-btn">
  <i class="modus-icons" style="font-size: 1.5rem;">add</i>
  <span>Add Item</span>
</button>
```

## Step 4: Use semantic HTML elements {{#semantic-html}}

> 💡 Always prefer **native HTML tags**—such as `<button>`, `<a>`, `<input>`, `<select>`—and decorate them with Modus utility classes. This keeps prototypes lightweight and ensures maximum compatibility with Gemini (and browsers that don't support Web Components).

```html
<!-- Primary action button -->
<button class="modus-wc-btn">Save</button>

<!-- Secondary button with icon -->
<button class="modus-wc-btn modus-wc-btn-secondary">
  <i class="modus-icons" style="font-size: 1.25rem;">save</i>
  <span>Save Draft</span>
</button>

<!-- Text input -->
<input type="text" class="modus-wc-input" placeholder="Your name" />

<!-- Select dropdown -->
<select class="modus-wc-select">
  <option>Option A</option>
  <option>Option B</option>
</select>
```
