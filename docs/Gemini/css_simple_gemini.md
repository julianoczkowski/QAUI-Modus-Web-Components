## Shared Base Values (Inherited by Classic Themes)

These properties are defined in the `:root` selector and are not overridden by the classic themes, so they apply to both `modus-classic-light` and `modus-classic-dark`.

### **Spacing**

- `--modus-wc-spacing-2xs`: `0.125rem`
- `--modus-wc-spacing-xs`: `0.25rem`
- `--modus-wc-spacing-sm`: `0.5rem`
- `--modus-wc-spacing-md`: `0.75rem`
- `--modus-wc-spacing-lg`: `1rem`
- `--modus-wc-spacing-xl`: `1.5rem`
- `--modus-wc-spacing-2xl`: `2rem`
- `--modus-wc-spacing-3xl`: `3rem`

### **Sizing (Font, Input, Border Width)**

- **Font Sizes:**
  - `--modus-wc-font-size-sm`: `0.75rem`
  - `--modus-wc-font-size-md`: `0.875rem`
  - `--modus-wc-font-size-lg`: `1rem`
  - `--modus-wc-font-size-xl`: `1.125rem`
  - `--modus-wc-font-size-2xl`: `1.25rem`
  - `--modus-wc-font-size-3xl`: `1.5rem`
- **Input Heights:**
  - `--modus-wc-input-height-sm`: `1.5rem`
  - `--modus-wc-input-height-md`: `2rem`
  - `--modus-wc-input-height-lg`: `3rem`
- **Border Widths:**
  - `--modus-wc-border-width-xs`: `1px`
  - `--modus-wc-border-width-sm`: `2px`
  - `--modus-wc-border-width-md`: `3px`
  - `--modus-wc-border-width-lg`: `4px`
  - `--modus-wc-border-width-xl`: `8px`
- **Other Component Sizing:**
  - `--tab-border`: `1px`

### **Radius (Base Defaults)**

- `--modus-wc-border-radius-sm`: `2px`
- `--modus-wc-border-radius-md`: `4px`
- `--modus-wc-border-radius-lg`: `8px`
- `--modus-wc-border-radius-xl`: `12px`
- `--rounded-badge`: `0.25rem`
- `--tab-radius`: `0.5rem`

### **Shadows**

Shadows are applied via utility classes rather than theme-specific variables. These values are consistent for both classic themes.

- **Button Shadow (`.modus-wc-btn`):** `0 1px 2px 0 rgba(0, 0, 0, 0.05)`
- **Modal Box Shadow (`.modus-wc-modal-box`):** `0 25px 50px -12px rgba(0, 0, 0, 0.25)`

---

## Modus Classic Light `[data-theme="modus-classic-light"]`

### **Colors**

- `--modus-wc-color-base-page`: `#fff` (white)
- `--modus-wc-color-base-100`: `#f1f1f6` (gray-light)
- `--modus-wc-color-base-200`: `#cbcdd6` (gray-1)
- `--modus-wc-color-base-300`: `#b7b9c3` (gray-2)
- `--modus-wc-color-base-content`: `#171c1e` (gray-10)
- `--modus-wc-color-info`: `#0063a3` (trimble-blue)
- `--modus-wc-color-success`: `#1e8a44` (green)
- `--modus-wc-color-error`: `#da212c` (red)
- `--modus-wc-color-warning`: `#fbad26` (yellow)
- `primary-focus`: `#004f83`
- `secondary-focus`: `#464b52`
- `accent-focus`: `#464b52`
- `neutral-focus`: `#a3a6b1`

### **Radius**

- `--rounded-btn`: `0.25rem`
- `--rounded-box`: `0.5rem`

---

## Modus Classic Dark `[data-theme="modus-classic-dark"]`

### **Colors**

- `--modus-wc-color-base-page`: `#000` (black)
- `--modus-wc-color-base-100`: `#252a2e` (trimble-gray)
- `--modus-wc-color-base-200`: `#464b52` (gray-8)
- `--modus-wc-color-base-300`: `#353a40` (gray-9)
- `--modus-wc-color-base-content`: `#cbcdd6` (gray-1)
- `--modus-wc-color-info`: `#0063a3` (trimble-blue)
- `--modus-wc-color-success`: `#1e8a44` (green)
- `--modus-wc-color-error`: `#da212c` (red)
- `--modus-wc-color-warning`: `#fbad26` (yellow)
- `primary-focus`: `#004f83`
- `secondary-focus`: `#e49325`
- `accent-focus`: `#464b52`
- `neutral-focus`: `#171c1e`

### **Radius**

- `--rounded-btn`: `0.25rem`
- `--rounded-box`: `0.5rem`
