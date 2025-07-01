---
tag: modus-wc-alert
category: Feedback & Messaging
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-alert--docs
---

> [!info] **SolidJS Quick Start**
>
> 1. **Import** `@trimble-oss/modus-web-components/modus-wc-styles.css` once in your entry file.
> 2. **Set** `document.documentElement.dataset.theme = "modus-classic-light"` before hydration to avoid a flash of the wrong theme (FOWT).
> 3. **Bind** arrays/objects with **property bindings** (`prop:*`) or a helper such as `useOptions`; _never_ pass JSON strings via attributes.

# Modus WC Alert

## Purpose

Displays contextual status messages—error, warning, success, info—optionally with a dismiss button, custom icon, and action content.

> **💡 Toast Integration:** This component is commonly used inside `modus-wc-toast` elements to create notification toasts. The alert provides the visual styling and content, while the toast handles positioning and timing.

## Attributes

- **`alert-title`** - `string` **(required)** - Headline text of the alert. _Reflected as prop_: **yes**
- **`alert-description`** - `string` - Longer descriptive text displayed under the title. _Reflected as prop_: **yes**
- **`variant`** - `"info" | "success" | "warning" | "error"` - Default: `"info"` - Sets colour scheme and default icon. _Reflected as prop_: **yes**
- **`dismissible`** - `boolean` - Default: `false` - Shows an "X" button that fires `dismissClick`. _Reflected as prop_: **yes**
- **`icon`** - `string` (Modus icon name) - Default: _auto-selected by variant_ - Overrides variant icon when supplied. _Reflected as prop_: **yes**
- **`role`** - `"alert" | "log" | "marquee" | "status" | "timer"` - Default: `"status"` - ARIA live-region semantics. _Reflected as prop_: **yes**
- **`custom-class`** - `string` - Default: `''` - Extra CSS class on the host element. _Reflected as prop_: **yes**

## Events

- **`dismissClick`** - `CustomEvent<void>` - Fires when the dismiss button is pressed.

## ⚠️ Common Mistakes

**Text not showing?** Make sure you're using the correct attributes:

```html
<!-- ❌ WRONG: Using 'title' instead of 'alert-title' -->
<modus-wc-alert title="This won't show" message="Neither will this">
</modus-wc-alert>

<!-- ❌ WRONG: Using 'text' or 'message' attributes -->
<modus-wc-alert text="This won't work" message="This won't work either">
</modus-wc-alert>

<!-- ❌ WRONG: Using 'type' instead of 'variant' -->
<modus-wc-alert type="success" message="This won't work either">
</modus-wc-alert>

<!-- ✅ CORRECT: Use 'variant' and 'alert-title' -->
<modus-wc-alert
  variant="success"
  alert-title="This will show!"
  alert-description="This description will also show."
>
</modus-wc-alert>

<!-- ✅ CORRECT: Minimum required is alert-title -->
<modus-wc-alert alert-title="This simple message will show"> </modus-wc-alert>
```

## Usage

### HTML Example

```html
<!-- Default (info) -->
<modus-wc-alert
  alert-title="New message!"
  alert-description="You have 3 new messages."
>
</modus-wc-alert>

<!-- Variant examples -->
<modus-wc-alert
  variant="success"
  alert-title="Success!"
  alert-description="Operation completed."
></modus-wc-alert>
<modus-wc-alert
  variant="warning"
  alert-title="Heads-up!"
  alert-description="Check the details."
></modus-wc-alert>
<modus-wc-alert
  variant="error"
  alert-title="Error!"
  alert-description="Something went wrong."
></modus-wc-alert>

<!-- Dismissible -->
<modus-wc-alert
  dismissible
  alert-title="Dismiss me"
  alert-description="Click the X to close."
></modus-wc-alert>

<!-- Custom icon -->
<modus-wc-alert
  icon="help"
  variant="info"
  alert-title="Need help?"
  alert-description="Visit our docs."
></modus-wc-alert>

<!-- Action button slot -->
<modus-wc-alert
  alert-title="New messages"
  alert-description="You have 3 unread messages."
>
  <modus-wc-button slot="button" color="secondary" variant="outlined" size="sm">
    View
  </modus-wc-button>
</modus-wc-alert>

<!-- Custom content slot -->
<modus-wc-alert variant="success">
  <div slot="content">
    <strong>Well done!</strong> You successfully read this important alert
    message.
  </div>
</modus-wc-alert>

<!-- Used inside a toast for notifications -->
<modus-wc-toast position="top-end" delay="4000">
  <modus-wc-alert
    variant="success"
    alert-title="Operation completed!"
    alert-description="Your data has been saved successfully."
    dismissible
  ></modus-wc-alert>
</modus-wc-toast>
```

### SolidJS Example

```tsx
// entry.tsx
import "@trimble-oss/modus-web-components/modus-wc-styles.css";
document.documentElement.dataset.theme = "modus-classic-light";

// AlertExample.tsx
import { createSignal, onMount } from "solid-js";

export function AlertExample() {
  const [isVisible, setIsVisible] = createSignal(true);
  let alertRef!: HTMLModusWcAlertElement;

  const handleDismiss = () => {
    setIsVisible(false);
  };

  return (
    <>
      {isVisible() && (
        <modus-wc-alert
          ref={alertRef}
          variant="success"
          alert-title="Operation Successful"
          alert-description="Your changes have been saved."
          prop:dismissible={true}
          on:dismissClick={handleDismiss}
        >
          <modus-wc-button
            slot="button"
            color="secondary"
            variant="outlined"
            size="sm"
          >
            View Details
          </modus-wc-button>
        </modus-wc-alert>
      )}

      <div style="margin-top: 1rem">
        {!isVisible() && (
          <modus-wc-button color="primary" on:click={() => setIsVisible(true)}>
            Show Alert Again
          </modus-wc-button>
        )}
      </div>
    </>
  );
}
```

> [!tip] **SolidJS Note**
> Boolean flags (`dismissible`, etc.) and all array/object props must be set with `prop:` directives, e.g. `prop:dismissible={isVisible()}`.

### Slot support

The component supports a **`button`** slot for action elements and a **`content`** slot when you omit `alert-title` / `alert-description` and provide fully custom markup instead.

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

## Pattern notes

- **Required text:** `alert-title` is REQUIRED for text to display. Don't use `title`, `text`, `message`, or `type` attributes.
- **Variant not type:** Use `variant="success"` not `type="success"` for alert styling.
- **Dismiss logic:** Listen for `dismissClick` to remove the element or update application state.
- **Icons:** Pass any Modus icon name to `icon`; leave blank to use the variant's default.
- **ARIA:** Set `role="alert"` for interruptive messages that should be announced immediately.
- **Live updates:** Because the component is a live region, DOM changes inside it will be announced by screen readers.
- **Toast usage:** When used inside `modus-wc-toast`, this component provides the message content and styling while the toast handles positioning and auto-dismissal timing.
