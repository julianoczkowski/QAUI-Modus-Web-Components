# Modus Icon System - Development Guidelines

## Icon Implementation

### Icon CDN Setup

```html
<!-- Modus Icons CDN -->
<link
  rel="preload"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/modus-outlined/fonts/modus-icons.css"
  as="style"
  crossorigin="anonymous"
/>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/modus-outlined/fonts/modus-icons.css"
/>
```

### Icon Usage Patterns

```html
<!-- Basic icon usage -->
<i class="modus-icons">icon_name</i>

<!-- Icon with text -->
<modus-wc-button>
  <i class="modus-icons" style="margin-right: 8px">download</i>
  Download
</modus-wc-button>

<!-- Icon-only button -->
<modus-wc-button shape="circle" aria-label="Delete item">
  <i class="modus-icons">delete</i>
</modus-wc-button>
```

## Icon Categories

### Navigation Icons

```html
<i class="modus-icons">arrow_left</i>
<i class="modus-icons">arrow_right</i>
<i class="modus-icons">arrow_up</i>
<i class="modus-icons">arrow_down</i>
<i class="modus-icons">chevron_left</i>
<i class="modus-icons">chevron_right</i>
<i class="modus-icons">chevron_up</i>
<i class="modus-icons">chevron_down</i>
```

### Action Icons

```html
<i class="modus-icons">add</i>
<i class="modus-icons">edit</i>
<i class="modus-icons">delete</i>
<i class="modus-icons">save_disk</i>
<i class="modus-icons">download</i>
<i class="modus-icons">upload</i>
<i class="modus-icons">refresh</i>
<i class="modus-icons">sync</i>
```

### Status Icons

```html
<i class="modus-icons">check</i>
<i class="modus-icons">close</i>
<i class="modus-icons">warning</i>
<i class="modus-icons">info</i>
<i class="modus-icons">alert</i>
<i class="modus-icons">help</i>
```

### UI Icons

```html
<i class="modus-icons">settings</i>
<i class="modus-icons">menu</i>
<i class="modus-icons">search</i>
<i class="modus-icons">filter</i>
<i class="modus-icons">sort</i>
<i class="modus-icons">more_vertical</i>
```

## Icon Styling

### Size Variations

```css
/* Icon sizes */
.icon-xs {
  font-size: 12px;
}
.icon-sm {
  font-size: 14px;
}
.icon-md {
  font-size: 16px;
}
.icon-lg {
  font-size: 20px;
}
.icon-xl {
  font-size: 24px;
}
```

### Color Variations

```css
/* Icon colors using Modus tokens */
.icon-primary {
  color: var(--modus-wc-color-primary);
}
.icon-secondary {
  color: var(--modus-wc-color-base-content);
}
.icon-success {
  color: var(--modus-wc-color-green);
}
.icon-warning {
  color: var(--modus-wc-color-yellow);
}
.icon-danger {
  color: var(--modus-wc-color-red);
}
```

### Icon Spacing

```css
/* Icon spacing utilities */
.icon-spacing-right {
  margin-right: 8px;
}
.icon-spacing-left {
  margin-left: 8px;
}
.icon-spacing-top {
  margin-top: 4px;
}
.icon-spacing-bottom {
  margin-bottom: 4px;
}
```

## Common Icon Patterns

### Button with Icon

```html
<!-- Icon + Text Button -->
<modus-wc-button color="primary">
  <i class="modus-icons" style="margin-right: 8px">save_disk</i>
  Save Changes
</modus-wc-button>

<!-- Icon-only Button -->
<modus-wc-button shape="circle" color="danger" aria-label="Delete item">
  <i class="modus-icons">delete</i>
</modus-wc-button>
```

### Navigation with Icons

```html
<!-- Breadcrumb with icons -->
<modus-wc-breadcrumbs>
  <modus-wc-breadcrumb href="/">
    <i class="modus-icons">home</i>
    Home
  </modus-wc-breadcrumb>
  <modus-wc-breadcrumb href="/projects">
    <i class="modus-icons">folder_open</i>
    Projects
  </modus-wc-breadcrumb>
  <modus-wc-breadcrumb>
    <i class="modus-icons">document</i>
    Current Project
  </modus-wc-breadcrumb>
</modus-wc-breadcrumbs>
```

### Status Indicators

```html
<!-- Status with icons -->
<div class="status-item">
  <i class="modus-icons" style="color: var(--modus-wc-color-green)"
    >check_circle</i
  >
  <span>Completed</span>
</div>

<div class="status-item">
  <i class="modus-icons" style="color: var(--modus-wc-color-yellow)">warning</i>
  <span>Pending</span>
</div>

<div class="status-item">
  <i class="modus-icons" style="color: var(--modus-wc-color-red)"
    >close_circle</i
  >
  <span>Failed</span>
</div>
```

## Icon Accessibility

### Screen Reader Support

```html
<!-- Decorative icons (hidden from screen readers) -->
<i class="modus-icons" aria-hidden="true">star</i>

<!-- Meaningful icons (include text alternative) -->
<i class="modus-icons" aria-label="Save document">save_disk</i>

<!-- Icon with visible text -->
<button>
  <i class="modus-icons" aria-hidden="true">download</i>
  <span>Download File</span>
</button>
```

### Focus Indicators

```css
/* Icon focus styles */
.icon-focusable:focus {
  outline: 2px solid var(--modus-wc-color-primary);
  outline-offset: 2px;
  border-radius: 2px;
}
```

## Icon Search & Discovery

### Icon Browser Implementation

```javascript
// Icon search functionality
function searchIcons(query) {
  const icons = document.querySelectorAll(".icon-item");
  const searchTerm = query.toLowerCase();

  icons.forEach((icon) => {
    const iconName = icon.dataset.iconName.toLowerCase();
    const isVisible = iconName.includes(searchTerm);
    icon.style.display = isVisible ? "block" : "none";
  });
}

// Copy icon name to clipboard
function copyIconName(iconName) {
  navigator.clipboard.writeText(iconName).then(() => {
    console.log(`Copied: ${iconName}`);
  });
}
```

### Icon Categories for Organization

```javascript
const iconCategories = {
  navigation: ["arrow_left", "arrow_right", "chevron_left", "chevron_right"],
  actions: ["add", "edit", "delete", "save_disk", "download", "upload"],
  status: ["check", "close", "warning", "info", "alert"],
  ui: ["settings", "menu", "search", "filter", "sort"],
  files: ["document", "folder_open", "folder_closed", "file_new"],
  communication: ["email", "chat", "phone", "notifications"],
};
```

## Icon Performance

### Icon Loading Optimization

```html
<!-- Preload critical icons -->
<link
  rel="preload"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/modus-outlined/fonts/modus-icons.css"
  as="style"
  crossorigin="anonymous"
/>

<!-- Lazy load non-critical icons -->
<i class="modus-icons lazy-load" data-icon="complex_icon"></i>
```

### Icon Caching

```javascript
// Cache frequently used icons
const iconCache = new Map();

function getIcon(iconName) {
  if (iconCache.has(iconName)) {
    return iconCache.get(iconName);
  }

  const iconElement = document.createElement("i");
  iconElement.className = "modus-icons";
  iconElement.textContent = iconName;

  iconCache.set(iconName, iconElement);
  return iconElement;
}
```

## Icon Testing

### Icon Rendering Test

```javascript
// Test if icons are loading correctly
function testIconRendering() {
  const testIcons = ["add", "edit", "delete", "save_disk", "download"];

  testIcons.forEach((iconName) => {
    const icon = document.createElement("i");
    icon.className = "modus-icons";
    icon.textContent = iconName;
    document.body.appendChild(icon);

    // Check if icon rendered correctly
    const computedStyle = window.getComputedStyle(icon);
    const fontFamily = computedStyle.fontFamily;

    console.log(
      `Icon ${iconName}: ${
        fontFamily.includes("modus-icons") ? "PASS" : "FAIL"
      }`
    );

    document.body.removeChild(icon);
  });
}
```

### Icon Accessibility Test

```javascript
// Test icon accessibility
function testIconAccessibility() {
  const icons = document.querySelectorAll(".modus-icons");

  icons.forEach((icon) => {
    const hasAriaLabel = icon.hasAttribute("aria-label");
    const hasAriaHidden = icon.hasAttribute("aria-hidden");
    const hasVisibleText =
      icon.nextElementSibling && icon.nextElementSibling.textContent.trim();

    if (!hasAriaLabel && !hasAriaHidden && !hasVisibleText) {
      console.warn("Icon may need accessibility improvements:", icon);
    }
  });
}
```

## Common Icon Issues

### Issue: Icons Not Displaying

**Solution**: Ensure CSS is loaded and font family is correct

```css
.modus-icons {
  font-family: "modus-icons" !important;
}
```

### Issue: Icon Spacing Problems

**Solution**: Use consistent spacing utilities

```css
.icon-with-text {
  margin-right: 8px;
}
```

### Issue: Icon Color Not Changing

**Solution**: Use CSS custom properties for theming

```css
.icon-themed {
  color: var(--modus-wc-color-primary);
}
```
